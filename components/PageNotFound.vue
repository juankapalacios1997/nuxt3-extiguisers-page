<template>
    <div class="container not-found-container">
        <img src="~/assets/images/fe25.jpg" alt="fe-sad"/>
        <div>
            <h2>Oops! It seems that the content that you were searching is no longer available</h2>
            <p>Please try again later</p>
        </div>
    </div>
</template>
<script>
export default {
    name: "PageNotFound"
}
</script>
<style scoped>
    .not-found-container {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 50 rem;
    }
    p {
        font-size: 18px;
    }
    img {
        width: 15rem;
        margin: 0 auto;
    }
</style>