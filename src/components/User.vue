<template>
    <div class="main__user" v-if="getUser" >
        <div class="main__user-left">
            <img :src="getUser.avatar_url" :alt="getUser.login">
            <a target="_blank" :href="getUser.html_url">ПОСЕТИТЬ</a>
        </div>
        <div class="main__user-right">
            <p>{{getUser.login}}</p>
            <p>Репозиториев: {{ getUser.public_repos }}</p>
            <p>Создан: {{ getUser.created_at }}</p>
            <p>Подписщиков: {{ getUser.followers }}</p>
            <p>Подписок: {{ getUser.following }}</p>
        </div>
    </div>
</template>

<script>
export default {
    computed: {
        getUser() {
          return this.$store.getters.getUserInfo
        }
    }
}
</script>

<style>

</style>