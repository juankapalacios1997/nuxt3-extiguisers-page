 <template>
    <div>
        <button id="show-btn" class="btn btn-primary w-100" @click="showModal">Rent me!</button>
        
        <div id="myModal" ref="myModal" class="modal fade" tabindex="-1" aria-labelledby="modalTitle" aria-hidden="true">
            <div class="modal-dialog">
                <div class="modal-content text-container">
                    <div class="modal-header">
                        <h5 class="modal-title" id="modalTitle">You are almost done!</h5>
                        <button type="button" class="btn-close" @click="hideModal"></button>
                    </div>
                    <div class="d-flex modal-body text-center">
                        <p class="me-3">Lorem, ipsum dolor sit amet consectetur adipisicing elit. 
                            Eligendi, rerum! Quaerat exercitationem soluta, doloribus iure numquam 
                            quae obcaecati. Maiores laudantium possimus quaerat! Repellat dignissimos 
                            magnam sequi nostrum maxime neque voluptatem.
                        </p>
                        <client-only>
                            <VDatePicker 
                            v-model.range="range"
                            :attributes="attrs"
                            />
                        </client-only>
                    </div>
                    <div class="modal-footer">
                        <button 
                        class="btn btn-danger w-100"
                        @click="onClickOrder(props.product.id)"
                        >
                            Order
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
    import { Modal } from "bootstrap";

    const store = useWebsiteStore();

    const props = defineProps({
        product: {
            type: Object,
            required: true,
        }
    })

    const range = ref({
        start: new Date(2022, 7, 15),
        end: new Date(2022, 7, 19)
    });

    const attrs = ref([
        {
            key: 'today',
            highlight: {
                color: 'green',
                fillMode: 'solid'
            },
            dates: new Date()
        }
    ])

    const myModal = ref<HTMLElement | null>(null);
    let modalInstance = ref<Modal | null>(null);

    onMounted(() => {
        if (myModal.value) {
            modalInstance.value = new Modal(myModal.value, { keyboard: true });
        }
    });

    const showModal = () => modalInstance.value?.show();
    const hideModal = () => modalInstance.value?.hide();
    const toggleModal = () => modalInstance.value?.toggle();
    
    const onClickOrder = (id:number):void => {
        store.addNewMyRental(id);
        toggleModal();
    }
</script>

<style scoped>
    .btn {
        width: 100%;
        border: none;
        padding: 0.5rem;
        font-weight: 700;
        padding: 1rem 4rem;
        border-radius: 100rem;
        font-weight: 700;
        transition: 0.5s;
    }
    .calendar-container {
        margin: 0 auto;
        display: flex;
        justify-content: space-between;
    }
    p {
        color: grey;
        text-align: justify;
    }
    .text-container {
        padding: 0.5rem
    }
</style>