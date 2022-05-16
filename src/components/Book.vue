<template>
  <div
    @dblclick="$emit('toggle-readIt', book.id)"
    :class="[book.readIt ? 'readIt' : '', 'book']"
  >
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
    <p>
      <i class="fa-solid fa-eye"></i>
      {{ book.readIt ? "Already Read it" : "Haven't read it yet" }}
    </p>
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
  padding: 10px 20px;
  cursor: pointer;
  position: relative;
  user-select: none;
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