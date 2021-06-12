<template>
  <div>
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
      <tr v-for="item in cartlist" :key="item.id">
        <td><input type="checkbox" /></td>
        <td>{{ item.id }}</td>
        <td>{{ item.name }}</td>
        <td>{{ item.price }}</td>
        <td>{{ item.count }}</td>
        <td><button>刪除</button></td>
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
        { id: 1, name: "細說台灣", price: 100, count: 1 },
        { id: 2, name: "細說台北", price: 80, count: 1 },
        { id: 3, name: "細說台中", price: 70, count: 1 },
        { id: 4, name: "細說台南", price: 75, count: 1 },
        { id: 5, name: "細說台東", price: 60, count: 1 },
      ],
    };
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
th, td {
  border: 1px solid #888888;
  padding: 10px;
}
</style>
