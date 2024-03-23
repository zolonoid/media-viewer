<template>
    <div class="content-filter-header">
        <div class="content-filter-header__panel">
            <ContentFilterPanel
                                :clearHidden="!selected.length"
                                @open="openFilters"
                                @close="closeFilters"
                                @clear="clearFilters" />
        </div>
        <div class="content-filter-header__quick-filters">
            <ContentFilterQuick
                                :quicks="quickFilters"
                                @onSelected="filterValueSelect" />
        </div>
    </div>
    <div class="content-filter-list-wrapper">
        <ContentFilterList v-if="curFilter"
                           :items="valueItems"
                           :prev="curFilter"
                           @onChange="filterSelect"
                           @navBack="closeFilterValues" />
        <ContentFilterList v-else
                           :items="filterItems"
                           navHidden
                           @onChange="filterSelect" />
    </div>
</template>

<script>
import ContentFilterPanel from './ContentFilterPanel.vue';
import ContentFilterQuick from './ContentFilterQuick.vue';
import ContentFilterList from './ContentFilterList.vue';
// state flags
const sf = {
    expand: 1,
    filters: 2,
    values: 4,
    selected: 8
}
export default {
    components: {
        ContentFilterPanel,
        ContentFilterQuick,
        ContentFilterList
    },
    props: {
        filters: Array, //{id,icon,title,values[]:{id,icon,title,quick}}
        //quicks: Array //{filterId,valueId}
    },
    emits: [
        "onFilter" //[{filterId,valueId}]
    ],
    data() {
        return {
            selected: [{ filterId: "", valueId: "" }],
            curFilter: undefined,
            filtersHidden: true
        };
    },
    computed: {
        quickFilters() {
            const quicks = [];
            for (const filter of this.filters) {
                for (const value of filter.values) {
                    if (value.quick)
                        quicks.push({
                            filterId: filter.id,
                            valueId: value.id,
                            valueIcon: value.icon,
                            selected: this.isFilterSelected(filter.id, value.id)
                        });
                }
            }
            return quicks;
        },
        filterItems() {
            return this.filters.map(x => ({
                id: x.id,
                icon: x.icon,
                title: x.title,
                selected: false
            }));
        },
        valueItems() {
            return this.curFilter
                ? this.curFilter.values.map(x => ({
                    id: x.id,
                    icon: x.icon,
                    title: x.title,
                    selected: this.isFilterSelected(curFilter.id, x.id)
                }))
                : [];
        }
    },
    methods: {
        filterSelect(filterId) {
            if (!this.curFilter)
                this.curFilter = this.filters.find(x => x.id === filterId);
            else
                this.filterValueSelect(this.curFilter.id, filterId);
        },
        filterValueSelect(filterId, valueId) {
            const index = this.selected.findIndex(x => x.filterId === filterId);
            if (index >= 0) {
                const unselected = this.selected.splice(index, 1);
                if (unselected[0].valueId === valueId) {
                    this.$emit("onFilter", this.selected);
                    return;
                }
            }
            this.selected.push({ filterId, valueId });
            this.$emit("onFilter", this.selected);
        },
        closeFilterValues() {
            this.curFilter = undefined;
        },
        openFilters() {
            this.filtersHidden = false;
        },
        closeFilters() {
            this.filtersHidden = true;
            this.closeFilterValues();
        },
        clearFilters() {
            this.selected = [];
            this.$emit("onFilter", this.selected);
        },
        isFilterSelected(filterId, valueId) {
            return this.selected.findIndex(x => x.filterId === filterId && x.valueId === valueId) >= 0;
        }
    },
}
</script>

<style lang="scss">
.content-filter-header {
    width: 100%;
    height: 20%;
    background-color: black;
    display: flex;
    justify-content: center;
    column-gap: 50px;

    &__panel {
        width: 50%;
    }

    &__quick-filters {
        width: 50%;
    }
}

.content-filter-list-wrapper {
    position: absolute;
    width: 100%;
    height: 80%;
    top: 20%;
    left: 0px;

    &_hidden {
        display: none;
    }
}
</style>