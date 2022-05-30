<template>
  <div class="container">
    <h1>📖 {{ showAddBook ? "Add a new Book" : "My Book List" }}</h1>
    <div class="header-btns">
      <button
        class="btn"
        @click="toggleAddBook"
        :style="{ background: showAddBook ? '#C73030' : '#34178c' }"
      >
        {{ showAddBook ? "Close x" : "Add Book +" }}
      </button>
      <button v-show="!showAddBook" class="btn" @click="updateView">
        {{ view == "list" ? "Table View" : "List View" }}
      </button>
    </div>

    <AddBook v-show="showAddBook" @add-book="addBook" />

    <div v-show="!showAddBook" class="books-container">
      <Books
        v-if="books && books.length > 0"
        @toggle-readIt="toggleReadIt"
        @delete-book="deleteBook"
        :books="books"
        :view="view"
      />
      <p v-else>Empty Book List...</p>
    </div>
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
      view: "list", //table
      books: [
        {
          id: 1,
          title: "History of Europe",
          cover:
            "https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-6-540x861.jpg",
          isRead: true,
          isbn: "0-395-07157-8",
          author: "Daniel Trejo",
        },
        {
          id: 2,
          title: "Penguin Classics",
          cover:
            "https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-2-540x861.jpg",
          isRead: false,
          isbn: "0-395-07157-8",
          author: "Daniel Trejo, Jon Snow",
        },
        {
          id: 3,
          title: "Becoming",
          cover:
            "https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-7-540x861.jpg",
          isRead: false,
          isbn: "0-395-07157-8",
          author: "Daniel Trejo",
        },
        {
          id: 4,
          title: "Sonnets",
          cover:
            "https://printpress.cmsmasters.net/default/wp-content/uploads/sites/11/2019/05/printpress-product-5-540x861.jpg",
          isRead: false,
          isbn: "0-395-07157-8",
          author: "Daniel Trejo",
        },
      ],
    };
  },
  methods: {
    toggleAddBook() {
      this.showAddBook = !this.showAddBook;
    },
    updateView() {
      this.view = this.view === "list" ? "table" : "list";
    },
    toggleReadIt(id) {
      this.books = this.books.map((book) => {
        if (book.id === id) {
          book.isRead = !book.isRead;
        }
        return book;
      });
    },
    addBook(book) {
      this.books.push(book);
    },
  },
};
</script>

<style>
@import "./assets/base.css";
</style>
