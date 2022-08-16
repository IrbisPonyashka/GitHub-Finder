<template>
  <main class="main">
    <div class="container main__container">
        <Search/>
        <div class="error" v-if="getError">
          <h2>{{ getError }}</h2>
        </div>
        <User/>
        <div class="sort" v-if="getRepos" >
          <Sort
            @cho="choose"
          />
        </div>
        <div class="repo" v-if="getRepos" >
          <RepoItem v-for="repo in getRepos" :key="repo.id" :repo="repo" />
        </div>
    </div>
  </main>
</template>

<script>

import Search from '@/components/Search.vue'
import User from '@/components/User.vue'
import RepoItem from '@/components/RepoItem.vue'
import Sort from '@/components/Sort.vue'

export default {
    data(){
      return{
        repos:[],
        statusChoose:'ИМЯ'
      }
    },
    components: {
        Search,
        User,
        RepoItem,
        Sort
    },
    methods:{
      choose(choos){
        this.statusChoose = choos;
      }
    },
    computed: {
        getError() {
          return this.$store.getters.getError
        },
        getRepos() {
          if(this.$store.getters.getRepos != null){
            if(this.statusChoose =='ИМЯ'){
              return this.$store.getters.getRepos.sort((a,b) => a.name.toLowerCase() > b.name.toLowerCase() ? 1 : -1);
            }else if(this.statusChoose=='ЗВЕЗДЫ'){
              return this.$store.getters.getRepos.sort((a,b) => a.stargazers_count < b.stargazers_count ? 1 : -1);
            }else if(this.statusChoose=='ДАТА'){
              return this.$store.getters.getRepos.sort((a,b) => a.created_at < b.created_at ? 1 : -1);
            }
          }else{
            return this.$store.getters.getRepos;
          }
        }
    }
}
</script>

<style>

</style>