<template>
  <div>
    <h2>Daftar Buku Yang Dibeli</h2>
    <div v-for="(book, index) in books" :key="index" class="book-item">
      <slot name="book" :book="book">
        <book-item-slot :book="book"></book-item-slot>
      </slot>
    </div>
    <div v-if="books.length === 0" class="no-books">Belum Ada Pembelian Buku</div>
  </div>
</template>

<script>
export default {
  name: 'BookList',
  props: {
    books: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      totalPrice: 0
    };
  },
  watch: {
    books: {
      handler(newVal) {
        this.calculateTotalPrice(newVal);
      },
      deep: true
    }
  },
  methods: {
    calculateTotalPrice(books) {
      this.totalPrice = books.reduce((total, book) => total + book.total, 0);
    }
  }
}
</script>

<style scoped>
.book-item {
  padding: 10px;
  border-bottom: 1px solid #ddd;
}

.no-books {
  text-align: center;
  margin-top: 20px;
  font-weight: bold;
  font-family: 'Dancing Script', cursive;
  color: white;
}

.total-price {
  font-weight: bold;
  text-align: center;
  margin-top: 20px;
}
</style>
