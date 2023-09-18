<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="book in books">
      <p>{{ book.title }}</p>
      <p>{{ book.author }}</p>
      <p>{{ book.pages }}</p>
      <hr />
    </div>
  </div>
</template>


<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "welcome to Vue.js!",
      books: []
    };
  },
  created: function() {
    this.getData()
  },
  methods: {
    getData: function(){
      axios.get("/books.json").then(response => {
        console.log(response.data)
        this.books = response.data
      })
    }
  }
};
</script>