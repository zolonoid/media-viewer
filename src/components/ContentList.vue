<template>
    <div class="content-list">
        <ContentListItem v-for="item in content" :key="item.id"
                         :type="item.type"
                         :preview="item.preview"
                         :title="item.title"
                         @itemClick="itemClickHandler(item)" />
    </div>
</template>

<script>
import ContentListItem from './ContentListItem.vue';
export default {
    components: {
        ContentListItem
    },
    props: {
        content: Array //{id,type,preview,title,src}
    },
    emits: [
        "contentClick" //{type,src}
    ],
    methods: {
        itemClickHandler(contentItem) {
            this.$emit("contentClick", { type: contentItem.type, src: contentItem.src });
        }
    },
}
</script>

<style lang="scss">
.content-list {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(max(100px, 30%), 1fr));
    grid-auto-rows: max-content;
    grid-gap: 5px;
    //box-sizing: border-box;
}
</style>
