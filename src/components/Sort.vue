<template>
    <div class="container">
    <div class="sort__select">
        <h2 class="sort__select-title">
            Сортировка
        </h2>
        <ul class="sort__select-list">
            <li v-for="el in list" :key="el.id" @click="giveClass(el.id), getChoose(el.text,el.class)" :class="el.class" >{{el.text}}</li>
        </ul>
    </div>
    </div>
</template>

<script>
export default {
    data(){
        return{
            choose:'',
            isActive:false,
            active:'',
            list:[{text:'ИМЯ',class:'sort__select-el active', id:1},{text:'ЗВЕЗДЫ',class:'sort__select-el', id:2},{text:'ДАТА',class:'sort__select-el', id:3}]
        }
    },
    methods:{
        giveClass(id){
            this.list.forEach(el => {
                if(id == el.id){
                    el.class += ' active'
                }else{
                    el.class = 'sort__select-el'
                }
            })
        },
        getChoose(text){
                    if(text == 'ИМЯ'){
                        this.$emit('cho',text)
                    }else if(text == 'ДАТА'){
                        this.$emit('cho',text)
                    }else if(text == 'ЗВЕЗДЫ'){
                        this.$emit('cho',text)
                    }
        }
    }
}
</script>

<style>

</style>
