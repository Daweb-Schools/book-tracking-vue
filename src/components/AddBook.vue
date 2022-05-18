<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Title</label>
      <input
        type="text"
        v-model="title"
        name="text"
        placeholder="Add Book Title"
      />
    </div>
    <div class="form-control">
      <label>Book Cover</label>
      <input type="text" v-model="cover" name="cover" placeholder="Add Cover" />
    </div>
    <div class="form-control">
      <label>Author</label>
      <input
        type="text"
        v-model="author"
        name="author"
        placeholder="Add Author"
      />
    </div>
    <div class="form-control">
      <label>ISBN#</label>
      <input type="text" v-model="isbn" name="isbn" placeholder="Add ISBN" />
    </div>
    <div class="form-control form-control-check">
      <input type="checkbox" v-model="readIt" name="readIt" id="readIt" />
      <label for="readIt">I have read it already</label>
    </div>

    <button type="submit" class="btn btn-block">Save Book</button>
  </form>
</template>

<script>
export default {
  name: "AddBook",
  data() {
    return {
      title: "",
      cover: "",
      author: "",
      isbn: "",
      readIt: false,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (!this.title) {
        alert("Please add a book");
        return;
      }
      const newBook = {
        id: Math.floor(Math.random() * 100000),
        title: this.title,
        cover: this.cover,
        author: this.author,
        isbn: this.isbn,
        readIt: this.readIt,
      };
      this.$emit("add-book", newBook);
      this.title = "";
      this.cover = "";
      this.author = "";
      this.isbn = "";
      this.readIt = false;
    },
    getFile(e) {
      console.log(e.target.files[0].mozFullPath);
    },
  },
};
</script>