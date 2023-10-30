<template>
  <div class="block__newContact">
    <div class="newContact">
      <div class="blockAddContact">
        <button class="addUser" @click="toggleForm">+</button>
      </div>
      <div class="newContact"><span>Новий контакт</span></div>
    </div>
    <form-new-contact :isVisible="showForm" @addNewContact="$emit('addNewContact',$event)" />
  </div>
</template>

<script>
import FormNewContact from "./FormNewContact.vue";
export default {
  name: "AddContactItem",
  components: { FormNewContact },
  data() {
    return {
      showForm: false,
    };
  },
  methods: {
    toggleForm() {
      this.showForm = !this.showForm;
    },
  },
};
</script>

<style lang="css" scoped>
.block__newContact {
  width: 90%;
  padding: 0px 0px 0px 10px;
}
.newContact {
  color: green;
  font-weight: 600;
  display: flex;
  align-items: center;
  gap: 10px;
}
.blockAddContact {
  padding: 4px;
  border-radius: 50%;
  border: 1px dashed green;
}
.blockAddContact:hover {
  border: 1px dashed rgb(255, 255, 255);
}
.addUser {
  border-radius: 50%;
  font-size: 20px;
  padding: 10px 15px;
  color: green;
  border: 0;
  background-color: white;
}
.addUser:hover {
  background-color: green;
  color: white;
}
</style>