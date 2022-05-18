<template>
  <div v-if="view == 'list'" class="books-list">
    <div :key="book.id" v-for="book in books">
      <book
        @toggle-readIt="$emit('toggle-readIt', book.id)"
        @delete-book="$emit('delete-book', book.id)"
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
          <td>{{ book.readIt ? "Already Read it" : "Haven't read it yet" }}</td>
        </tr>
      </tbody>
    </table>
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
  emits: ["delete-book", "toggle-readIt"],
};
</script>