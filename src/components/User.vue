<template>
    <div className="users">
            <button @click="deleteUser(index)">Delete</button>
            <h3 className="users__name"> {{ user.name }}</h3>
            <p className="user__info"> {{  user.email }} - {{ user.pass }}</p>
    </div>
</template>

<script>
    export default{
        props: {
            user: { 
                type: Object,
                required: true,
             },
             index: {
                type: Number,
                required: true,
             },
             deleteUser: {
                type: Function,
                required: true,
             }
        }
    }
</script>

<style scoped>

</style>