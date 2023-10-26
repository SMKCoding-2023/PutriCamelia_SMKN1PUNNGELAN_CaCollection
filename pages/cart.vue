<template>
  <div class="container mt-5">
    <div v-if="cartItems.length === 0" class="alert alert-info">
      Keranjang belanja Anda kosong.
    </div>
    <div v-else>
      <h2>Keranjang Belanja</h2>
      <table class="table">
        <thead>
          <tr>
            <th>Produk</th>
            <th>Harga</th>
            <th>Jumlah</th>
            <th>Total</th>
            <th>Aksi</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in cartItems" :key="index">
            <td>{{ item.name }}</td>
            <td>$ {{ item.price }}</td>
            <td>
              <input type="number" v-model="item.quantity" min="1" @input="updateCart" />
            </td>
            <td>$ {{ item.quantity * item.price }}</td>
            <td>
              <button class="btn btn-danger" @click="removeItem(index)">Hapus</button>
            </td>
          </tr>
        </tbody>
      </table>
      <h3>Total: $ {{ total }}</h3>
      <button class="btn btn-primary" @click="checkout">Checkout</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cartItems: [
        { name: 'KACAMATA', price: 150000, quantity: 1 },
        { name: 'TOPI PANTAI', price: 100000, quantity: 1 },
        { name: 'STRIPED PATTERN SCARF', price: 300000, quantity: 1 },
        { name: 'PERHIASAN', price: 1000000, quantity: 1 },
        { name: 'SELOP JAWA', price: 100000, quantity: 1 },
        { name: 'GETA', price: 150000, quantity: 1 },
        { name: 'TEROMPAH', price: 100000, quantity: 1 },
        { name: 'ZORI', price: 200000, quantity: 1 },
        { name: 'KIMONO', price: 350000, quantity: 1 },
        { name: 'HANBOOK', price: 400000, quantity: 1 },
        { name: 'KEBAYA', price: 300000, quantity: 1 },
        { name: 'ULOS', price: 200000, quantity: 1 },
        { name: 'RANSEL', price: 85000, quantity: 1 },
        { name: 'TAS SELEMPANG', price: 80000, quantity: 1 },
        { name: 'HANDBAG', price: 90000, quantity: 1 },
        { name: 'DOMPET', price: 55000, quantity: 1 },
      ],
    };
  },
  computed: {
    total() {
      return this.cartItems.reduce((total, item) => total + item.quantity * item.price, 0);
    },
  },
  methods: {
    updateCart() {
    },
    removeItem(index) {
    },
    checkout() {
      alert('Checkout berhasil!');
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-bottom: 20px;
}

th, td {
  border: 1px solid #ccc;
  padding: 10px;
  text-align: left;
}

th {
  background-color: #f2f2f2;
}

.btn {
  cursor: pointer;
  margin-right: 10px;
}

.btn-primary {
  background-color: #007bff;
  color: #fff;
  border: none;
}

.btn-danger {
  background-color: #dc3545;
  color: #fff;
  border: none;
}

.alert {
  padding: 15px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

.alert-info {
  background-color: #d1ecf1;
  border-color: #bee5eb;
  color: #0c5460;
}

.alert-success {
  background-color: #d4edda;
  border-color: #c3e6cb;
  color: #155724;
}

h2 {
  margin-bottom: 20px;
}

h3 {
  margin-top: 20px;
}
</style>