<template>
  <div class="wrapper__contacts">
    <contact-item
      v-for="contact in contactsData"
      :key="contact.activity_score"
      :contactData="contact"
    />
  </div>
</template>

<script>
import ContactItem from "./ContactItem.vue";
export default {
  name: "ContactsList",
  components: { ContactItem },
  props: {
    contactsData: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="css" scoped>
.wrapper__contacts {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>