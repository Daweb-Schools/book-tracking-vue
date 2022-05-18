<template>
  <div class="book">
    <div v-show="book.readIt" class="readIt">
      <i class="fa-solid fa-eye"></i>
    </div>
    <div class="book-cover">
      <img :src="book.cover" />

      <button @click="$emit('toggle-readIt', book.id)">
        <i class="fa-solid fa-eye"></i>
        <span>
          {{ book.readIt ? "Already Read it" : "Haven't read it yet" }}</span
        >
      </button>
    </div>
    <div class="book-details">
      <p class="book-author">{{ book.author }}</p>
      <h3 class="book-title">
        {{ book.title }}
      </h3>
      <p><i class="fa-solid fa-hashtag icon"></i> {{ book.isbn }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Book",
  props: {
    book: Object,
  },
};
</script>