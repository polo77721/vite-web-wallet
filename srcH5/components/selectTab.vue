<template>
    <div class="select-tab-wrapper">
        <span class="select-tab" :class="{'active': activeTab === key}"
              v-for="(tab, key) in tabList" :key="key"
              @click="selectTab(key)">{{ $t(tab) }}</span>
    </div>
</template>

<script>
export default {
    props: {
        tabList: {
            type: Object,
            default: () => {}
        },
        defaultTab: {
            type: String,
            default: ''
        }
    },
    data() {
        return { activeTab: this.defaultTab };
    },
    methods: {
        selectTab(tab) {
            this.activeTab = tab;
            this.$emit('input', this.activeTab);
        }
    }
};
</script>

<style lang="scss" scoped>
@import "~h5Assets/scss/vars.scss";

.select-tab-wrapper {
    display: inline-block;
    position: relative;
    left: 50%;
    transform: translateX(-50%);
    border-radius: 2px;
    font-size: 12px;
    @include font-bold();
    color: rgba(255,255,255,1);
    line-height: 18px;

    .select-tab {
        box-sizing: border-box;
        display: inline-block;
        height: 30px;
        line-height: 30px;
        white-space: nowrap;
        text-align: center;
        color: $blue;
        border: 1px solid $blue;
        &.active {
            position: relative;
            top: -1px;
            border: none;
            background: $blue;
            color: #fff;
        }
    }
}
</style>
