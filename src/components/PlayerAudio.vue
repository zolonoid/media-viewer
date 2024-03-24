<template>
    <div class="player-audio">
        <audio controls autoplay :src="audioSrc"></audio>
    </div>
</template>

<script>
export default {
    props: {
        audioSrc: String
    }
}
</script>

<style lang="scss">
.player-audio {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: end;
}
</style>