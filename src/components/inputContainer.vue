<template>
    <div class="input-controller">
        <div class="d-flex form-items">
  <input v-on:keyup="findMeaning()"    type="text" class="form-control" placeholder="Search your word" v-model="word">
  <button @click="findMeaning()" class="btn btn-primary" type="button">Search</button>
</div>
    
        <resultVue v-if="showResult" :word=word :sound=sound :meanings=meanings></resultVue>
    </div>
</template>
<script>
    import resultVue from './result.vue';
    export default{
        name:'inputContainer',
        components:{
            resultVue
        },
        data(){
            return{
                word:null,
                sound:null,
                meanings:null,
                showResult:false,
            }
        },
        methods:{
            async findMeaning(){
                const data=await fetch("https://api.dictionaryapi.dev/api/v2/entries/en/"+this.word);
                const words=await data.json();
                this.sound=words[0].phonetic;
                this.showResult=true;
                console.log(words);
                this.meanings=words[0].meanings;
            }
        }
    }
</script>

<!-- script file.. -->
<style scoped>
  .input-controller{
    margin-left:300px;
    margin-top:30px;
    margin-right:200px;
    background-color: #095869;
    border:1px solid #095874;
}
input{
    margin-right: 5px;
}
.form-items{
    margin-top:10px;
    margin-left:5px;
    margin-right:5px;
}
</style>
