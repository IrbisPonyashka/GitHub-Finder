<template>
  <div class="repo__item">
    <div class="repo__item-left">
        <h2 class="repo__item-title">{{ repo.name }}</h2>
        <p class="repo__item-stars">Кол-во звёзд: {{ repo.stargazers_count }} ⭐</p>
        <p class="repo__item-date">
            Дата добавления: 
            {{ new Date(repo.created_at).toLocaleDateString() }}
            </p>
    </div>
    <div class="repo__item-right">
        <a :href="repo.html_url" target="_blank" class="repo__item-link">ПОСЕТИТЬ</a>
    </div>
  </div>
</template>

<script>
export default {
    props: ['repo']
}
</script>

<style>

</style>