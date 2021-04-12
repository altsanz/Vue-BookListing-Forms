<template>
  <form class action="#" method="post" v-on:submit.prevent="bookSubmit(bookData)">
    <input type="text" name="title" value v-model="bookData.bookTitle" placeholder="Book Title" />
    <input type="text" name="author" value v-model="bookData.bookAuthor" placeholder="Book Author" />
    <div>
      <input name="finishedReading" type="checkbox" v-model="bookData.finishedReading" />
      <label for="finishedReading">Finished reading</label>
      <input name="borrowed" type="radio" value="borrowed" v-model="bookData.ownership" />
      <label for="borrowed">Borrowed</label>
      <input name="bought" type="radio" value="bought" v-model="bookData.ownership" />
      <label for="bought">Bought</label>
    </div>
    <button type="submit" name="button">Add Book</button>
  </form>
</template>

<script>
export default {
  name: "BookForm",
  props: ["books"],
  data() {
    return {
      bookData: {
        bookTitle: "",
        bookAuthor: "",
        finishedReading: false,
        ownership: []
      }
    };
  },
  methods: {
    bookSubmit(bookData) {
      this.$emit("addBook", bookData);
    }
  }
};
</script>

<style scoped>
</style>
