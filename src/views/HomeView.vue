    <script>
    export default {
        data() {
            return {
                newTodo: '',
                todos: [],
                filter: 'all'
            };
        },
        computed: {
            filteredTodos() {
                if (this.filter === 'all') {
                    return this.todos;
                } else if (this.filter === 'isTodo') {
                    return this.todos.filter(todo => todo.isDone);
                } else if (this.filter === 'notTodo') {
                    return this.todos.filter(todo => !todo.isDone);
                }
            }
        },
        methods: {
            addTodo() {
                if (this.newTodo.trim() !== '') {
                    this.todos.push({
                        text: this.newTodo,
                        isDone: false,
                        editing: false
                    });
                    this.newTodo = '';
                }
            },
            toggleDone(index) {
                this.todos[index].isDone = !this.todos[index].isDone;
            },
            editTodo(index) {
    if (this.todos[index].text.trim() !== '') { // 檢查待辦事項是否為空
        this.todos[index].editing = !this.todos[index].editing;
    } else {
        // 提示用戶待辦事項不能為空
        alert('待辦事項不能為空');
    }
},

            deleteTodo(index) {
                this.todos.splice(index, 1);
            },
            filterTodos(filter) {
                this.filter = filter;
            }
        }
    };
    </script>
<template>
  <div class="w-full h-screen bg-indigo-500 flex justify-center items-center">
    <div class="w-1/2 bg-white rounded-lg shadow-lg p-8">
        <div class="mb-4 flex items-center">
            <input class="input-text mr-4 w-2/3 px-3 py-2 border border-gray-300 rounded-lg" type="text" v-model="newTodo" placeholder="新增待辦事項">
            <button class="bg-indigo-600 text-white px-4 py-2 rounded-lg" @click="addTodo">新增</button>
        </div>
        <div class="mb-4">
            <button class="filter-btn" :class="{ 'active': filter === 'all' }" @click="filterTodos('all')">全部</button>
            <button class="filter-btn" :class="{ 'active': filter === 'isTodo' }" @click="filterTodos('isTodo')">已完成</button>
            <button class="filter-btn" :class="{ 'active': filter === 'notTodo' }" @click="filterTodos('notTodo')">未完成</button>
        </div>
        <div class="flex items-center border-b border-gray-300 py-2">
            <div class="w-1/4 font-bold">狀態</div>
            <div class="w-1/2 font-bold">事項</div>
            <div class="w-1/4 font-bold">操作</div>
        </div>
        <div v-for="(todo, index) in filteredTodos" :key="index" class="flex items-center border-b border-gray-300 py-2">
            <div class="w-1/4">{{ todo.isDone ? '已完成' : '未完成' }}</div>
            <div class="w-1/2">
                <input v-if="!todo.editing" type="text" v-model="todo.text" readonly class="input-text">
                <input v-else type="text" v-model="todo.text" class="input-text">
            </div>
            <div class="w-1/4 flex justify-end items-center">
                <button class="edit-btn" @click="editTodo(index)">{{ todo.editing ? '儲存' : '編輯' }}</button>
                <button class="delete-btn" @click="deleteTodo(index)">刪除</button>
                <button class="done-btn" @click="toggleDone(index)">{{ todo.isDone ? '未完成' : '完成' }}</button>
            </div>
        </div>
    </div>
  </div>
</template>


<style scoped>
.input-text {
    border: 1px solid #ccc;
    border-radius: 4px;
    padding: 0.5rem;
    width: 100%;
}

.filter-btn {
    background-color: #4a90e2;
    color: #fff;
    border: none;
    border-radius: 4px;
    padding: 0.5rem 1rem;
    margin-right: 0.5rem;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

.filter-btn.active {
    background-color: #185adb;
}

.edit-btn,
.delete-btn,
.done-btn,
button 
{
    background-color: #4a90e2;
    color: #fff;
    border: none;
    border-radius: 4px;
    padding: 0.3rem 0.5rem;
    margin-left: 0.5rem;
    cursor: pointer;
    transition: background-color 0.3s ease;
    white-space:nowrap;
}

.edit-btn:hover,
.delete-btn:hover,
.done-btn:hover {
    background-color: #185adb;
}
</style>
