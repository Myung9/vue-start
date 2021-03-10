<template>
    <form v-on:submit.prevent="submitForm">
      <div>
        <label for="username">id: </label>
        <input id="username" type="text" v-model="username">
      </div>
      <div>
        <label for="password">password : </label>
        <input id="password" type="password" v-model="password">
      </div>
      <button type="submit">login</button>
    </form>
</template>

<script>
import axios from 'axios';

export default {
  //데이터가 공유되지 않게 새로운 객체를 만들게 function
  data: function() {
    return {
      username: '',
      password: '',
    }
  },
  methods: {
    submitForm: function() {
      // event.preventDefault();
      console.log(this.username, this.password);
      var url = 'https://jsonplaceholder.typicode.com/users';
      var data = {
        username: this.username,
        password: this.password
      }
      axios.post(url, data)// post : 데이터를 생성하거나 조작할때 사용하는 http method
        .then(function(response){
          console.log(response);
        })
        .catch(function(error){
          console.log(error);
        });
    }
  }
}
</script>

<style>

</style>