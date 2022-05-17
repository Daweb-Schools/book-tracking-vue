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

    <input type="submit" value="Save Book" class="btn btn-block" />
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
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check {
  display: flex;
  align-items: center;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
.form-control input[type="checkbox"] {
  width: auto;
  flex: unset;
  height: 20px;
}
</style>