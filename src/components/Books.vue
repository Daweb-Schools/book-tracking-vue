<template>
  <div v-if="view == 'list'" class="books-list">
    <div :key="book.id" v-for="book in books">
      <book
        @toggle-readIt="$emit('toggleReadIt', book.id)"
        :book="book"
      />
    </div>
  </div>
  <div v-if="view == 'table'">
    <table>
      <thead>
        <tr>
          <th>Title</th>
          <th>Author</th>
          <th>ISBN#</th>
          <th>Read it?</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="book in books" :key="book.id">
          <td>{{ book.title }}</td>
          <td>{{ book.author }}</td>
          <td>{{ book.isbn }}</td>
          <td><input type="checkbox" id="checkbox" v-model="book.isRead" /></td>
        </tr>
      </tbody>
    </table>
  </div>

  <div class="books-read">
    <label for="file">Your Progress</label><br/>
    <progress :class="{complete : this.booksReadPercent >= 100}" :value="booksReadPercent" max="100"> </progress>
    <p>{{booksReadMesage}}</p>
  </div>

</template>

<script>
import Book from "./Book.vue";
export default {
  name: "Books",
  props: {
    books: Array,
    view: String,
  },
  components: {
    Book,
  },
  emits: ["toggleReadIt"],
  computed: {
    booksRead() {
      return this.books.filter(book => book.isRead).length;
    },
    booksReadPercent() {
      return Math.round(this.booksRead / this.books.length * 100);
    },
    booksReadMesage() {
      return this.booksReadPercent >=100 
      ? 'All the books were read. Congrats!' 
      : `${this.booksRead} out of ${this.books.length} books were read`;
    },
  }
};
</script>