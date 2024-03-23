<template>
    <div class="content-filter-list-item"
         :class="{ 'content-filter-list-item_selected': selected }"
         @click="itemClick">
        <div class="content-filter-list-item__icon"
             :style="{ backgroundImage: `$url('${iconUrl}')` }">
            {{ title }}
        </div>
    </div>
</template>

<script>
export default {
    props: {
        itemId: String,
        iconUrl: String,
        title: String,
        selected: Boolean
    },
    emits: [
        "onSelect"
    ],
    methods: {
        itemClick() {
            this.$emit("onSelect", itemId);
        }
    },
}
</script>

<style lang="scss">
.content-filter-list-item {
    width: 100%;
    aspect-ratio: 3 / 1;
    display: flex;
    align-items: center;
    border: 1px solid white;

    &_selected {
        border-color: green;
    }

    &__icon {
        height: 90%;
        aspect-ratio: 1 / 1;
        background-size: 100% 100%;
    }

    &__title {
        height: 90%;
        background-color: azure;
        padding: 10%;
        text-align: center;
    }
}
</style>
