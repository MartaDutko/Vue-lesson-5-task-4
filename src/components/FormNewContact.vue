<template>
    <div class="block__addForm" v-if="isVisible">
        <label>Firstname<input type="text" v-model="firstName"></label>
        <label>Lastname<input type="text" v-model="lastName"></label>
        <label>Email<input type="email" v-model="email"></label>
        <div class="addBtn"><button @click="addContact">Add</button></div>
    </div>
</template>

<script>
    export default {
        name:'FormNewContact',
    data() {
        return {
            firstName: null,
            lastName: null,
            email:null
        }
    },
    props: {
        isVisible: {
            type: Boolean,
            default: false
        },
    },
    methods: {
        addContact() {
            const obj={
                first_name:this.firstName,
                last_name:this.lastName,
                emails:[this.email]
            }
            this.$emit('addNewContact',obj)
        }
    },
    }
</script>

<style lang="css" scoped>
.block__addForm{
    display: flex;
    flex-direction: column;
    align-items: end;
    gap: 10px;
}
label{
    color: green;
}
input{
    margin:0 0 0 5px;
}
button{
    border: 0;
    border-radius: 5px;
    padding: 5px 20px;
    cursor: pointer;
}
button:hover{
    background-color: green;
    color: white;
}
</style>