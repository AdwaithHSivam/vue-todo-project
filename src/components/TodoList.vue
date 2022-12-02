<script setup>
import { reactive, ref } from 'vue';
import TodoItemVue from './TodoItem.vue'
import PlusIcon from './icons/IconPlus.vue';
const lastId = ref(2);
const addText = ref("")
const items = ref([
    {
        'id': 1,
        'text': 'Pick up Laundry',
        'completed': false,
    },
    {
        'id': 2,
        'text':'Mow the lawn',
        'completed':true,
    },
])

function deleteItem(id) {
    items.value = items.value.filter(item => item.id!==id)
}

function addItem() {
    if (addText.value !== "") {
        items.value.push({
            id: ++lastId.value,
            text: addText.value,
            completed: false,
        })
    }
    addText.value = ""
}

</script>

<template>
    <form>
        <input v-model="addText" placeholder="Todo" class="todo_input"/>
        <button
            class="add_btn"
            @click.prevent="addItem"
        >
            <i><PlusIcon/></i>
        </button>
    </form>
    <div class="todo_container">
        <ul class="todo_list">
            <TodoItemVue
                v-for="item in items"
                :id="item.id"
                :text="item.text"
                :completed="item.completed"
                :key="item.id"
                @delete="deleteItem(item.id)"
                @complete="(item.completed=!item.completed)"
            />
        </ul>
    </div>
    
</template>

<style scoped>
form{
    display: flex;
    min-height: 15vh;
    justify-content: center;
    align-items: center;    
}
form input, form button{
    padding: 0.4rem;
    border: none;
    font-size: 1.6rem;
    /* background: white; */
}
.todo_container{
    display: flex;
    justify-content: center;
    align-items: center;
}
.todo_list{
    min-width: 40%;
    list-style: none;
}
</style>
