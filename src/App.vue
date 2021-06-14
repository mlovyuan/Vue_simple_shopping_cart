<template>
  <div v-if="cartlist.length <= 0">
    尚未添加商品至購物車，購物車為空。
  </div>
  <div v-else>
    <table>
      <caption>
        Shopping Cart
      </caption>
      <tr>
        <th></th>
        <th>編號</th>
        <th>商品名稱</th>
        <th>商品價格</th>
        <th>商品數量</th>
        <th>操作</th>
      </tr>
      <tr v-for="(item, index) in cartlist" :key="item.id">
        <td><input type="checkbox" v-model="item.checkbox" /></td>
        <td>{{ item.id }}</td>
        <td>{{ item.name }}</td>
        <td><small>$</small>{{ item.price }}</td>
        <td>
          <button @click="item.count--" :disabled="item.count <= 1">-</button>
          {{ item.count }}
          <button @click="item.count++">+</button>
        </td>
        <td><a href="#" @click.prevent="deleteGood(index)">刪除</a></td>
      </tr>
      <tr>
        <td colspan="3" align="right">總價</td>
        <td colspan="3">{{ totalPrice }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      cartlist: [
        { id: 1, name: "細說台灣", price: 100, count: 1, checkbox: true },
        { id: 2, name: "細說台北", price: 80, count: 1, checkbox: true },
        { id: 3, name: "細說台中", price: 70, count: 1, checkbox: true },
        { id: 4, name: "細說台南", price: 75, count: 1, checkbox: true },
        { id: 5, name: "細說台東", price: 60, count: 1, checkbox: true },
      ],
    };
  },
  computed: {
    totalPrice: {
      get() {
        return (
          "$" +
          this.cartlist
            .filter((x) => x.checkbox == true)
            .reduce((a, b) => a + b.price * b.count, 0)
          // this.cartlist.reduce((a, b) => {
          //   if (b.checkbox) return a + b.price * b.count;
          //   else return a;
          // }, 0)
        );
      },
    },
  },
  methods: {
    deleteGood(index) {
      this.cartlist.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
table {
  width: 600px;
  border: 1px solid #888888;
  border-collapse: collapse;
}
th,
td {
  border: 1px solid #888888;
  padding: 10px;
}
th {
  background: #ccc;
}
</style>
