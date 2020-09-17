  
<template>
  <form
    v-on:submit.prevent="bookSubmit(bookTitle, bookAuthor)"
    class
    action="#"
    method="post"
    @submit.prevent="bookSubmit(bookData)"
  >
    <input v-model="bookTitle" type="text" name="title" value placeholder="Book Title" />
    <input v-model="bookAuthor" type="text" name="author" value placeholder="Book Author" />
    <div>
      <label for="finishedReading">
        <input
          type="checkbox"
          name="finishedReading"
          id="finishedReading"
          v-model="bookData.finishedReading"
        />
        Finished Reading
      </label>
    </div>
    <div>
      <label for="borrowed">
        <input
          type="radio"
          name="ownership"
          id="borrowed"
          value="borrowed"
          v-model="bookData.ownership"
        />
        borrowed
      </label>
      <label for="borrowed">
        <input
          type="radio"
          name="ownership"
          id="bought"
          value="bought"
          v-model="bookData.ownership"
        />
        bought
      </label>
    </div>
    <button type="submit" name="button">Add Book</button>
  </form>
</template>

<script>
export default {
  name: "BookForm",
  props: ["books"],
  data() {
    return {
      bookData: {
        bookTitle: "",
        bookAuthor: "",
        finishedReading: false,
        ownership: [],
      },
    };
  },
  methods: {
    bookSubmit(bookTitle, bookAuthor) {
      this.$emit("addBook", bookTitle, bookAuthor);
    },
  },
};
</script>

<style></style>