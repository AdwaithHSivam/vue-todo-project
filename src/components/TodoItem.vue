<script setup>
import CheckIcon from './icons/IconCheck.vue';
import UncheckIcon from './icons/IconUncheck.vue';
import DeleteIcon from './icons/IconDelete.vue';
defineProps(['id', 'text', 'completed']);
defineEmits(['complete', 'delete'])
</script>

<template>
    <div 
        class="todo"
        :class="{completedItem:completed}"
    >
        <li class="todo_item">{{text}}</li>
        <button
            v-if="completed"
            class="complete_btn"
            @click="$emit('complete')"
        >
            <i><CheckIcon/></i>
        </button>
        <button
            v-else
            class="complete_btn"
            @click="$emit('complete')"
        >
            <i><UncheckIcon/></i>
        </button>
        <button 
            class="delete_btn"
            @click="$emit('delete')"
        >
            <i><DeleteIcon/></i>
        </button>
        
    </div>
</template>

<style scoped>

.todo{
    margin: 5px auto;
    /* background: white;
    color: #000000; */
    display: flex;
    font-size: 1.2rem;
    padding: 0.3rem;
    justify-content: space-between;
    align-items: center;
    transition: all 0.5s ease;
}

.todo li {
    flex: 1;
}

/* STYLING THE BUTTONS ON THE TASKS  */
.complete_btn, 
.delete_btn{
    padding: 0.5rem;
    /* color: white; */
    border: none;
    margin-left: 0.2rem;
    cursor: pointer;
    font-size: 1rem;
}

/* .complete_btn{
    background: #43b343;
}
.complete_btn:active{
    background: green;
} */

/* .delete_btn{
    background: #ff3700;
}
.delete_btn:active{
    background: #b65337;
} */

.completedItem{
    text-decoration: line-through;
    opacity: 0.9;
    /* transform: scale(0.96); */
}
</style>
