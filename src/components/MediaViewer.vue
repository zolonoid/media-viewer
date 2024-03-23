<template>
    <div class="media-viewer"
         :style="{ width: position.mainWidth, height: position.mainHeght }">
        <div class="media-viewer__player">

        </div>
        <div class="media-viewer__nav-left">

        </div>
        <div class="media-viewer__nav-right">

        </div>
        <div class="media-viewer__content"
             :style="{ width: position.contentWidth, height: position.contentHeght }">
            <ContentManager
                            :content="config.content"
                            :filters="config.filters"
                            @filterChange="filterChangeHandler"
                            @contentPlay="contentPlayHandler"
                            @contentEnd="contentEndHandler" />
        </div>
    </div>
</template>

<script>
import ContentManager from './ContentManager.vue';
import PlayerAudio from './PlayerAudio.vue';
import PlayerVideo from './PlayerVideo.vue';
import PlayerImage from './PlayerImage.vue';

export default {
    components: {
        ContentManager,
        PlayerAudio,
        PlayerVideo,
        PlayerImage
    },
    props: {
        config: Object, //{content[]:{id,type,preview,title,src},filters[]:{id,icon,title,values[]:{id,icon,title,quick}}
        position: Object  //{place,mainWidth,mainHeght,contentWidth,contentHeght}}
    },
    emits: [
        "filterChange",
        "contentEnd"
    ],
    methods: {
        filterChangeHandler(selected) {
            this.$emit("filterChange", selected);
        },
        contentPlayHandler(contentInfo) {

        },
        contentEndHandler() {
            this.$emit("contentEnd");
        }
    },
}
</script>

<style lang="scss">
.media-viewer {
    position: relative;

    &__player {
        height: 100%;
    }

    &__nav-left,
    &__nav-right {
        position: absolute;
        height: 100%;
    }

    &__content {
        position: absolute;

        &_hidden {
            display: none;
        }

        &_right {
            width: 100%;
            top: 0px;
            left: 100%;
        }

        &_bottom {
            top: 100%;
            left: 0px;
        }
    }

    // &_cm-inner{

    // }
    // &_cm-fullscreen{

    // }
}
</style>