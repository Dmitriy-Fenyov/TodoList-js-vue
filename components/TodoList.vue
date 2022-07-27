<template>
<div>

<ul>
    
    <Todoitem 
    v-for="todo of todos"
    v-bind:todo="todo"
    />
</ul>

</div>

</template>

<script>

import Todoitem from './Todoitem.vue'
export default {
    props: ['todos'],
    components: {
    Todoitem
} 
}
</script>

<style scoped>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
    }

</style>