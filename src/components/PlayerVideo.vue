<template>
    <div class="player-video">
        <video controls autoplay :src="videoSrc"></video>
    </div>
</template>

<script>
export default {
    props: {
        videoSrc: String
    }
}
</script>

<style lang="scss">
.player-video {
    width: 100%;
    height: 100%;
}
</style>