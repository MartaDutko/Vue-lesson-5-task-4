<template>
  <div class="block__contactItem">
    <div class="logoItem">
      <div>{{ getLogo }}</div>
    </div>
    <div class="informationItem">
      <p class="tittleInformation">{{ getSender }}</p>
      <p class="messageItem">{{ contactData.emails[0] }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "ContactItem",
  props: {
    contactData: {
      type: Object,
      default: () => ({}),
    },
  },
  computed: {
    // Перевірка на наясність імені в відправнника
    isExistSender() {
      return this.contactData.first_name && this.contactData.last_name;
    },
    // Вивід logo для відправника
    getLogo() {
      if (this.isExistSender) {
        return (
          this.contactData.first_name[0] + this.contactData.last_name[0]
        ).toUpperCase();
      } else {
        return this.contactData.emails[0].slice(0, 3).toUpperCase();
      }
    },
    // Вивід повідомлення
    getSender() {
      if (this.isExistSender) {
        return this.contactData.first_name + " " + this.contactData.last_name;
      } else {
        return this.contactData.emails[0];
      }
    },
  },
};
</script>

<style lang="css" scoped>
p {
  margin: 0;
  padding: 0;
}
.block__contactItem {
  width: 100%;
  padding: 5px 10px;
  border-radius: 5px;
  display: flex;
  align-items: center;
  gap: 10px;
  cursor: pointer;
}
.block__contactItem:hover {
  background-color: rgb(236, 236, 236);
}
.logoItem {
  border-radius: 50%;
  width: 50px;
  height: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(180, 99, 255);
}
.logoItem div {
  font-weight: 600;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
}
.informationItem {
  width: 70%;
  text-align: left;
}
.tittleInformation {
  font-size: 20px;
}
.messageItem {
  color: rgb(108, 106, 106);
}
</style>