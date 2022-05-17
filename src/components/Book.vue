<template>
  <div :class="[book.readIt ? 'readIt' : '', 'book']">
    <img class="book-cover" :src="book.cover" />
    <div class="book-details">
      <div class="book-title">
        <h3>
          <i class="fa-solid fa-book icon"></i>
          {{ book.title }}
        </h3>
        <div @click="$emit('delete-book', book.id)">
          <i class="fa-solid fa-xmark"></i>
        </div>
      </div>
      <p><i class="fa-solid fa-user icon"></i> {{ book.author }}</p>
      <p><i class="fa-solid fa-hashtag icon"></i> {{ book.isbn }}</p>
      <p @click="$emit('toggle-readIt', book.id)">
        <i class="fa-solid fa-eye"></i>
        {{ book.readIt ? "Already Read it" : "Haven't read it yet" }}
      </p>
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

<style scope>
.fas {
  color: red;
}
.book {
  background: #f4f4f4;
  margin: 20px 5px;

  cursor: pointer;
  position: relative;
  user-select: none;
  display: flex;
}

.book-cover {
  width: 140px;
  object-fit: cover;
}

.book-details {
  padding: 10px 20px;
  display: flex;
  flex-direction: column;
  width: 100%;
}

.book.readIt {
  border-bottom: 5px solid #1cab47;
}
.book h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.book .book-title {
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
}

.book .book-title .icon {
  margin-right: 10px;
}

.book .readIt-layout {
  position: absolute;
  bottom: 0;
  right: 0;
  color: #210a66;
  font-size: 20px;
  padding: 6px;
}
</style>