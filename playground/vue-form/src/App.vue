<template>
  <!-- event.preventDefault(); 랑 같은 역할 -->
  <form v-on:submit.prevent="submitForm">
    <div>
      <label for="username">id:</label>
      <input
        id="username"
        type="text"
        v-model="username"
        placeholder="아이디"
      />
    </div>
    <div>
      <label for="password">password</label>
      <input
        id="passwrod"
        type="password"
        v-model="password"
        placeholder="비번"
      />
    </div>
    <button type="submt">login</button>
  </form>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    submitForm: function () {
      // event.preventDefault(); // 새로고침 막는 방법
      console.log(this.username, this.password);
      var url = "https://jsonplaceholder.typicode.com/users";
      var data = {
        username: this.username,
        password: this.password,
      };
      axios
        .post(url, data)
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>

<style>
</style>