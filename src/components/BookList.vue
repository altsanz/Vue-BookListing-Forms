<template>
  <div>
    <h1>{{ title }}</h1>
    <ul>
      <book-item v-for="book in books" :book="book" v-bind:key="book.title"></book-item>
      <book-form @addBook="appendBook"></book-form>
    </ul>
    <hr>
    <h2>Filtered Books By Ownership</h2>
    <select name="holding" id="holding" v-model="holding">
      <option v-for="filter in filters" v-bind:key="filter" :value="filter">{{ filter }}</option>
    </select>
        <ul>
      <book-item v-for="book in filteredBooks" :book="book" v-bind:key="book.title"></book-item>
    </ul>
  </div>
</template>


<script>
import _ from "lodash";
import BookItem from './BookItem';
import BookForm from './BookForm';

export default {
  name: "BookList",
  data() {
    return {
      title: "All Books",
      books: [
        { title: "Self-Reliance", author: "Ralph Waldo Emerson", finishedReading: true, ownership: "borrowed" },
        { title: "American Gods", author: "Neil Gaiman", finishedReading: false, ownership: "bought" },
        { title: "Amusing Ourselves to Death", author: "Neil Postman", finishedReading: true, ownership: "borrowed" }
      ],
      filters: ["bought", "borrowed"],
      holding: "bought"
    };
  },
  computed: {
    filteredBooks() {
      return _.filter(this.books, ['ownership', this.holding]);
    }
  },
  methods: {
      appendBook: function (bookData) {
          this.books.push({ title: bookData.bookTitle, author: bookData.bookAuthor, finishedReading: bookData.finishedReading, ownership: bookData.ownership});
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
