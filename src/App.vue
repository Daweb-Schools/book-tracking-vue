<template>
  <div class="container">
    <h1>📖 My Book List</h1>
    <button
      class="btn header-btn"
      @click="toggleAddBook"
      :style="{ background: showAddBook ? '#C73030' : '#34178c' }"
    >
      {{ showAddBook ? "Close x" : "Add Book +" }}
    </button>

    <AddBook v-if="showAddBook" @add-book="addBook" />

    <Books
      v-if="books && books.length > 0"
      @toggle-readIt="toggleReadIt"
      @delete-book="deleteBook"
      :books="books"
    />
    <p v-else>Empty Book List...</p>
  </div>
</template>

<script>
import Books from "./components/Books.vue";
import AddBook from "./components/AddBook.vue";

export default {
  name: "App",
  components: {
    Books,
    AddBook,
  },
  data() {
    return {
      showAddBook: false,
      books: [],
    };
  },
  methods: {
    toggleAddBook() {
      this.showAddBook = !this.showAddBook;
    },
    deleteBook(id) {
      console.log(id);
      if (confirm("Are you sure?")) {
        this.books = this.books.filter((book) => book.id !== id);
      }
    },
    toggleReadIt(id) {
      this.books = this.books.map((book) =>
        book.id === id ? { ...book, readIt: !book.readIt } : book
      );
    },
    addBook(book) {
      this.books = [...this.books, book];
    },
  },
};
</script>

<style>
@import "./assets/base.css";

.container h1 {
  margin-bottom: 20px;
}
.container .header-btn {
  position: absolute;
  top: 0;
  right: 10px;
  margin: 0;
  border-radius: 0 0 15px 15px;
}
</style>
