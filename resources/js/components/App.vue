<template>
    <div>
        <h1 class="center-text">لیست خرید</h1>
        <div class="todoListContainer">
            <add-item-form />
            <list-view />
        </div>
    </div>
</template>

<script>
import addItemForm from './addItemForm'
import listView from './listView'

export default {
    components: {
        addItemForm,
        listView,
    }
}
</script>
<style scoped>
    .todoListContainer{
        width: 400px;
        margin: auto;
        margin-top: 50px;
    }
    .center-text {
        margin-top:100px;
        text-align:center;   
    }
</style>
