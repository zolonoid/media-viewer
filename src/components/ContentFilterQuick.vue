<template>
    <div class="content-filter-quick">
        <div v-for="item in quicks" :key="item.filterId + item.valueId"
             class="content-filter-quick__item"
             :class="{ 'content-filter-quick__item_selected': item.selected }"
             :style="{ backgroundImage: `$url('${item.icon}')` }"
             @click="filterClick(item.filterId,item.valueId)">
        </div>
    </div>
</template>

<script>
export default {
    props: {
        quicks: Array //{filterId,valueId,icon,selected}
    },
    emits: [
        "onSelected"
    ],
    methods: {
        filterClick(filterId, valueId) {
            this.$emit("onSelected", { filterId, valueId });
        }
    },
}
</script>

<style lang="scss">
.content-filter-quick {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    column-gap: 10px;

    &__item {
        height: 90%;
        aspect-ratio: 1 / 1;
        background-size: 100% 100%;
        background-repeat: no-repeat;
        border: 1px solid white;
        border-radius: 5px;

        &_selected {
            border-color: green;
        }
    }
}
</style>
