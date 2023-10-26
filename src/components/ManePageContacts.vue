<template>
  <div class="weapper__contact">
    <filter-contact @clickSearck="filterClick"/>
    <add-contact-item @addNewContact="addNewContact" />
    <contacts-list :contactsData="listContacts" />
  </div>
</template>

<script>
import AddContactItem from "./AddContactItem.vue";
import ContactsList from "./ContactsList.vue";
import FilterContact from './FilterContact.vue';
export default {  
  name: "ManePageContacts",
  components: { ContactsList, AddContactItem, FilterContact },

  props: {
    listContacts: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    addNewContact(obj) {
      this.$emit('addNewContact', obj);
    },
    filterClick(element){
    this.$emit('clickSearck',element)
  }
  },

};
</script>

<style lang="css" scoped>
.weapper__contact{
  width: 50%;
  display: flex;
  flex-direction: column;
  gap: 15px;
}
</style>