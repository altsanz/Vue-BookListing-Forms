<template>
  <div>
    <h1>{{ title }}</h1>
    <ul>
      <book-item v-for="book in books" :book="book" v-bind:key="book.title"></book-item>
      <book-form @addBook="appendBook"></book-form>
    </ul>
  </div>
</template>


<script>
import BookItem from './BookItem';
import BookForm from './BookForm';

export default {
  name: "BookList",
  data: () => {
    return {
      title: "All Books",
      books: [
        { title: "Self-Reliance", author: "Ralph Waldo Emerson" },
        { title: "American Gods", author: "Neil Gaiman" },
        { title: "Amusing Ourselves to Death", author: "Neil Postman" }
      ]
    };
  },
  methods: {
      appendBook: function (bookData) {
          this.books.push({ title: bookData.bookTitle, author: bookData.bookAuthor});
      }
  },
  components: {
      BookItem,
      BookForm
  }
};
</script>

<style scoped>
h1,
h2 {
  font-weight: normal;
}

ul {
    list-style-type: none;
    padding: 0;
}


</style>
