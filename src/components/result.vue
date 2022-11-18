<template>
    <div class="result">
        <div class="row-items d-flex">
        <h4 class="text-light">Word: {{ word }} ({{ sound }})</h4>
        
        </div>
        <h4 class="text-light">Meanings</h4>
        <div class="meaning" v-for="meaning in meanings">
            <h5 class="text-light meaning-title">{{meaning.partOfSpeech}}</h5>
            <listedDataVue :meaning=meaning.definitions></listedDataVue>
        </div>
    </div>
</template>

<script>
    import listedDataVue from './listedData.vue';
    export default{
        name:'result',
        props:{
            word:String,
            sound:String,
            meanings:Array,
        },
        components:{
            listedDataVue
        }
    }
</script>
<style>
    .result{
        margin-left:10px;
        margin-top: 10px;
    }
    .meaning-title{
        margin-left: 10px;
        text-decoration: underline;
    }
    

</style>