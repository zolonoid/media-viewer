<template>
    <div class="player-image">
        <img :src="imageSrc" alt="">
    </div>
</template>

<script>
export default {
    props: {
        imageSrc: String
    }
}
</script>

<style lang="scss">
.player-image {
    width: 100%;
    height: 100%;
}
</style>