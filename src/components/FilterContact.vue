<template>
  <div class="block__filter">
    <input type="text" placeholder="Пошук" v-model="searcUser"/>
    <button class="searchBtn" @click="search">🔎</button>
  </div>
</template>

<script>
export default {
  name: "FilterContact",
  data() {
    return {
        searcUser: null
    }
  },
  methods: {
    search() {
        this.$emit('clickSearck', this.searcUser)
    }
  },
};
</script>

<style lang="css" scoped>
.block__filter {
  width: 90%;
  display: flex;
}
input {
  width: 90%;
  border: 0;
  border-bottom: 1px solid gray;
}
.searchBtn {
  font-size: 20px;
  cursor: pointer;
  border: 0;
  padding: 0 10px;
  background-color: white;
}
.searchBtn:hover {
  border-radius: 5px;
  background-color: rgb(224, 224, 224);
}
input:focus {
  outline: none;
}
</style>