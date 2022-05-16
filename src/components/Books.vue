<template>
  <div :key="book.id" v-for="book in books">
    <book
      @toggle-readIt="$emit('toggle-readIt', book.id)"
      @delete-book="$emit('delete-book', book.id)"
      :book="book"
    />
  </div>
</template>

<script>
import Book from "./Book.vue";
export default {
  name: "Books",
  props: {
    books: Array,
  },
  components: {
    Book,
  },
  emits: ["delete-book", "toggle-readIt"],
};
</script>