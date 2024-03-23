<template>
    <div class="content-manager">
        <ContentFilter
                       :filters="filters"
                       @onFilter="filterHandler" />
        <div class="content-manager__content">
            <ContentList
                         :content="content"
                         @contentClick="contentClickHandler" />
        </div>
    </div>
</template>

<script>
import ContentFilter from './ContentFilter.vue';
import ContentList from './ContentList.vue';
export default {
    components: {
        ContentFilter,
        ContentList
    },
    props: {
        content: Array, //{id,type,preview,title,src}
        filters: Array //{id,icon,title,values[]:{id,icon,title,quick}}
    },
    emits: [
        "filterChange", //[{filterId,valueId}]
        "contentPlay", //{type,src}
        "contentEnd"
    ],
    computed: {

    },
    methods: {
        filterHandler(selected) {
            this.$emit("filterChange", selected);
        },
        onContentEnd() {
            this.$emit("contentEnd");
        },
        contentClickHandler(contentInfo) {
            this.$emit("contentPlay", contentInfo);
        }
    },

}
</script>

<style lang="scss">
.content-manager {
    position: relative;
    width: 100%;
    height: 100%;

    &__content {
        height: 80%;
        position: absolute;
        top: 20%;
        left: 0px;
        width: 100%;
    }
}
</style>