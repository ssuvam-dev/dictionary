<template>
 <ul class="text-light" v-for='data in meaning'>
          
            <li>{{data.definition}}</li>
 </ul>
</template>
<script>
 
    export default{
        name:'listedData',
        props:{
            meaning:Object
        },
       
    }
</script>