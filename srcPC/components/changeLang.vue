<template>
    <div class="common-list-wrapper  __pointer">
        <span class="list-title" :class="{
            'down': !showLang,
            'up': showLang
        }" @click="toggleLangList">{{ $t('lang') }}</span>
        <ul class="list" v-show="showLang">
            <li v-for="(key, index) in messages" v-show="key.lang !== $t('lang')" :key="index"
                @click="changeLocale(index)">{{key.lang}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    data() {
        return {
            showLang: false,
            messages: this.$i18n.messages
        };
    },
    methods: {
        toggleLangList() {
            this.showLang = !this.showLang;
        },
        changeLocale(locale) {
            this.$i18n.locale = locale;
            window.viteWalletI18n && window.viteWalletI18n.setLocale(locale);
            this.$store.commit('setLang', locale);
            this.toggleLangList();
        }
    }
};
</script>

<style lang="scss" scoped>
@import "~pcAssets/scss/list/start.scss";
@import "~pcAssets/scss/list/setting.scss";
</style>
