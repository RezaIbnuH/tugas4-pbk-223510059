<template>
  <div class="book-item">
    {{ book.title }} Ditulis Oleh {{ book.author }} Dengan Harga Rp{{ book.price }} <br>
    Jumlah Buku Yang Dibeli {{ book.quantity }} <br>
    Harga Total Rp{{ book.total }}
  </div>
</template>

<script>
export default {
  name: 'BookItemSlot',
  props: {
    book: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.book-item {
  padding: 10px;
  border-bottom: 1px solid #ddd;
  font-weight: bold;
  font-family: 'Dancing Script', cursive;
  color: white;
}
</style>
