<template>
  <div class="about">
    <h1>This is an about page</h1>
    <ul class="item" v-for="item in list" :key="item.id">
      <li>{{ item.id }}</li>
      <li>{{ item.email }}</li>
      <li>{{ item.first_name }} {{ item.last_name }}</li>
      <li>
        <img :src="item.avatar" />
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HomeView",
  data() {
    return {
      list: [],
    };
  },

  async mounted() {

    let result = await axios.get("https://reqres.in/api/users?page=1");
    console.log(result.data.data);
    this.list = result.data.data;
  },
};
</script>

<style>
.item {
  display: flex;
  justify-content: center;
}

@media only screen and (min-width: 600px) {
  .item {
    background-color: green;
  }
}

.item li {
  display: inline-block;
  border: 1px solid black;
  width: 180px;
  text-align: center;
  padding: 5px;
}

@media only screen and (min-width: 600px) {
  .item li {
    background-color: yellow;
  }
}

.item img {
  width: 50px;
}

@media only screen and (min-width: 600px) {
  .item img {
    background-color: lightblue;
  }
}
</style>
