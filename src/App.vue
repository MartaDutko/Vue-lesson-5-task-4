<template>
  <mane-page-contacts
    :listContacts="contactListUser"
    @addNewContact="addContact"
    @clickSearck="filterContact"
  />
</template>

<script>
import ManePageContacts from "./components/ManePageContacts.vue";
import { contacts } from "./constants/7_data_contacts";

export default {
  components: { ManePageContacts },
  name: "App",
  data() {
    return {
      contacts,
      filterContacts: null,
    };
  },
  methods: {
    validObject(obj) {
      return obj.first_name && obj.last_name && obj.emails;
    },
    addContact(obj) {
      if (this.validObject(obj)) this.contacts.push(obj);
    },

    // Метод фільтрування
    searchFilterElement(el, searchElement) {
      let first_name = el.first_name
        ? el.first_name.includes(searchElement)
        : false;
      let last_name = el.last_name
        ? el.last_name.includes(searchElement)
        : false;
      let emails = el.emails.some((emeil) => emeil.includes(searchElement));
      return first_name || last_name || emails
    },
    // Метод який фільтрує по кліку
    filterContact(searchElement) {
      if (searchElement) {
        this.filterContacts = this.contacts.filter((el) => {
          if (el.first_name || el.last_name || el.emails) {
          return this.searchFilterElement(el, searchElement);
          }
        });
      }
    },
  },
  computed: {
    // Метод, який передає відповідно до умови props в компонент
    contactListUser() {
      if(this.filterContacts)return this.filterContacts
      else return this.contacts
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: center;
}
</style>
