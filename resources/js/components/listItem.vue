<template>
    <div class="item">
        <input type="checkbox" @change="updateTodo()" v-model="item.completed">
        <span :class="['itemText', item.completed? 'completed' : '']">{{ item.todo }}</span>
        <button class="edit">
            <font-awesome-icon icon="edit"/>
        </button>
        <button class="delete" @click="removeTodo()">
            <font-awesome-icon icon="trash"/>
        </button>
    </div>
</template>

<script>
export default {
    props: ['item'],
    methods: {
        updateTodo() {
            axios.post('api/todo/update/'+this.item.id, {
                completed: this.item.completed
            }).then(response => {
                if(response.status >= 200 && response.status < 300 ){
                    alert('Item Udpate Succesfully')
                    this.$emit('ReloadTodos')
                }
            })

        },
        removeTodo() {
            axios.get('api/todo/delete/' + this.item.id).then(response =>{
                if(response.status >= 200 && response.status < 300 ){
                    alert('Item Deleted Succesfully')
                    this.$emit('ReloadTodos')
                }
            })
        }
    }
}
</script>

<style>
    .item{
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .completed {
        text-decoration: line-through;
        color: #999999;
    }
    .itemText {
        width: 100%;
        margin-right: 20px;
        text-align: right;
    }
    .edit {
        color: blue;
        border-radius: 5px;
        border: none;
        outline: none;
        margin-right: 5px;
        background-color: white;
        font-size: 17px;

    }
    .delete {
        color: red;
        border-radius: 5px;
        border: none;
        outline: none;
        background-color: white;
        font-size: 17px;
    }
</style>