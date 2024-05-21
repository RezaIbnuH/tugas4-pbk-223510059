<template>
  <div class="app">
    <header>
      <h1>Toko Buku</h1>
    </header>
    <book-form @add-book="addBook"></book-form>
    <book-list :books="books">
      <template #book="{ book }">
        <book-item-slot :book="book"></book-item-slot>
      </template>
    </book-list>
    <div class="totals">
      <h2>Total Harga Buku: {{ totalPrice }}</h2>
    </div>
  </div>
</template>

<script>
import BookForm from './components/BookForm.vue';
import BookList from './components/BookList.vue';
import BookItemSlot from './components/BookItemSlot.vue';

export default {
  name: 'App',
  components: {
    BookForm,
    BookList,
    BookItemSlot
  },
  data() {
    return {
      books: []
    };
  },
  computed: {
    totalPrice() {
      return this.books.reduce((total, book) => total + book.total, 0);
    }
  },
  methods: {
    addBook(book) {
      this.books.push(book);
    }
  }
}
</script>

<style>
body {
  background-image: url(./assets/Lib.jpg);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}

.app {
  padding: 20px;
  max-width: 1000px;
  margin: auto;
  background-color: transparent;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

header {
  text-align: center;
  margin-bottom: 20px;
}

.totals {
  text-align: center;
  margin-top: 20px;
  font-weight: bold;
}

h1, h2 {
  font-family: 'Dancing Script', cursive;
  color: white;
  font-size: 3em;
}

button {
  background-color: #3498db;
  color: black;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 5px;
}

button:hover {
  background-color: #2980b9;
}
</style>
