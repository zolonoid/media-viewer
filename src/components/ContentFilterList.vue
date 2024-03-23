<template>
    <div class="content-filter-list">
        <div class="content-filter-list__nav"
             :class="{ 'content-filter-list__nav_hidden': navHidden }">
            <div class="content-filter-list__nav-back"
                 @click="backClick">
                <svg fill="#ffffff" height="100%" width="100%" viewBox="0 0 512.00 512.00" xml:space="preserve"
                     stroke="#ffffff" stroke-width="15.36">
                    <path
                          d="M256,5.333C114.88,5.333,0,117.76,0,256s114.88,250.667,256,250.667S512,394.24,512,256S397.12,5.333,256,5.333z M256,485.333C126.613,485.333,21.333,382.4,21.333,256S126.613,26.667,256,26.667S490.667,129.493,490.667,256 S385.387,485.333,256,485.333z">
                    </path>
                    <path
                          d="M337.387,381.013c-0.107-0.107-0.32-0.213-0.427-0.32L167.36,256l169.6-124.8c4.8-3.413,5.76-10.133,2.347-14.827 c-3.52-4.8-10.133-5.76-14.933-2.24L143.04,247.467c-4.693,3.52-5.76,10.133-2.24,14.933c0.64,0.853,1.387,1.6,2.24,2.24 l181.333,133.227c4.693,3.627,11.307,2.773,14.933-1.92C342.933,391.253,342.08,384.64,337.387,381.013z">
                    </path>
                </svg>
            </div>
            <div class="content-filter-list__nav-title">
                {{ prev.title }}
            </div>
        </div>
        <div class="content-filter-list__items">
            <div v-for="item in items" :key="item.id">
                <ContentFilterListItem
                                       :itemId="item.id"
                                       :iconUrl="item.icon"
                                       :title="item.title"
                                       :selected="item.selected"
                                       @onSelect="itemSelect" />
            </div>
        </div>
    </div>
</template>

<script>
import ContentFilterListItem from './ContentFilterListItem.vue'

export default {
    components: {
        ContentFilterListItem
    },
    props: {
        items: Array, //{id,icon,title,selected}
        navHidden: Boolean,
        prev: Object //{id,title}
    },
    emits: [
        "onChange",
        "navBack"
    ],
    methods: {
        backClick() {
            this.$emit("navBack");
        },
        itemSelect(itemId) {
            this.$emit("onChange",itemId);
        }
    }
}
</script>

<style lang="scss">
.content-filter-list {
    width: 100%;
    height: 100%;

    &__nav {
        display: flex;

        &_hidden {
            display: none;
        }

        &-back {
            width: 25%;
            aspect-ratio: 1 / 1;
        }

        &-title {
            width: 75%;
            height: 100%;
            text-overflow: ellipsis;
            white-space: nowrap;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
        }
    }

    &__items {
        display: flex;
        flex-direction: column;
        gap: 10px;
    }

    &__item {
        width: 100%;
    }
}
</style>
