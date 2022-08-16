<template>
    <div class="main__search">
        <input 
            type="text"
            class="main__search-input"
            placeholder="Введите имя пользователя"
            v-model="search"
            @keydown.enter="getUser"
        >
        <img @click="clear" src="@/assets/close.svg" alt="" class="main__search-close" v-if="search.length">
        <button @click="getUser" class="main__search-btn">НАЙТИ</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            search: ''
        }
    },
    methods: {
        clear() {
            this.search = ''
        },
        getUser() {
            this.$store.dispatch('getUserInfo', this.search)
            this.search = ''
        }
    }
}
</script>

<style>

</style>