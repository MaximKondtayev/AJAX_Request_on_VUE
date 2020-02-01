<template>
    <form class="search">
        <input 
            type="text"
            :value="moviTitle"
            @keyup="handleChange"
        />
        <input @click="handleSubmit" type="submit" value="SEARCH">
    </form>
</template>

<script>
import {ref} from '@vue/composition-api';

export default {
   name: 'Search',
   props: ['search'],
   setup ({search}, {emit}){
       const moviTitle = ref(search);

       return {
           moviTitle,
           handleSubmit(event) {
               event.preventDefault();
               emit('search', moviTitle.value)
           },
           handleChange(event) {
               moviTitle.value = event.target.value
           }
       }
   } 
};
</script>