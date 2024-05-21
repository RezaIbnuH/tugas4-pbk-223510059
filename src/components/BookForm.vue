<template>
  <div class="form-container">
    <h2>Form Pembelian Buku</h2>
    <form @submit.prevent="submitForm" class="book-form">
      <div class="form-group">
        <label for="title">Judul Buku</label>
        <input type="text" v-model="title" class="form-control" placeholder="Masukkan judul buku">
      </div>
      <div class="form-group">
        <label for="author">Pengarang</label>
        <input type="text" v-model="author" class="form-control" placeholder="Masukkan pengarang buku">
      </div>
      <div class="form-group">
        <label for="price">Harga Buku</label>
        <input type="number" v-model.number="price" class="form-control" placeholder="Masukkan harga buku">
      </div>
      <div class="form-group">
        <label for="quantity">Jumlah Buku</label>
        <input type="number" v-model.number="quantity" class="form-control" placeholder="Masukkan jumlah buku">
      </div>
      <button type="submit" class="btn">Tambah Buku</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'BookForm',
  data() {
    return {
      title: '',
      author: '',
      price: '',
      quantity: ''
    };
  },
  methods: {
    submitForm() {
      const total = this.price * this.quantity;
      const book = {
        title: this.title,
        author: this.author,
        price: this.price,
        quantity: this.quantity,
        total: total
      };
      this.$emit('add-book', book);
      this.clearForm();
    },
    clearForm() {
      this.title = '';
      this.author = '';
      this.price = 0;
      this.quantity = 1;
    }
  }
}
</script>

<style scoped>
.form-container {
  max-width: 800px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 5px;
  background-color: #f9f9f9;
}

h2 {
  font-family: 'Dancing Script', cursive;
  color: black;
  font-size: 2.5em;
}

.book-form {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

label {
  font-weight: bold;
  font-family: 'Dancing Script', cursive;
}

input {
  width: 100%;
  padding: 10px;
  box-sizing: border-box;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
  font-weight: bold;
  font-family: 'Dancing Script', cursive;
}

button:hover {
  background-color: #2980b9;
}
</style>
