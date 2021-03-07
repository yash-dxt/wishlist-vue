<template>
  <Header
    @delete-all="deleteAll"
    @add-random="addRandom"
    @show-add-task="showAddTask"
  />
  <div v-show="showAddWishList"><AddItem @add-wish="addWish" /></div>

  <WishList
    @delete-item="deleteItem"
    @toggle-urgent="toggleUrgent"
    :wishlist="wishlist"
  />
</template>

<script>
import Header from "./components/Header.vue";
import WishList from "./components/WishList.vue";
import AddItem from "./components/AddItem.vue";
export default {
  name: "App",
  components: {
    Header,
    WishList,
    AddItem,
  },
  data() {
    return {
      wishlist: [],
      showAddWishList: false,
    };
  },
  methods: {
    addRandom() {
      this.wishlist = [
        ...this.wishlist,
        {
          id: Math.floor(Math.random() * 100000),
          wish: `${Math.floor(Math.random() * 100000)} wish`,
          urgent: Math.floor(Math.random() * 100000) % 2 == 0 ? false : true,
        },
      ];
    },
    showAddTask() {
      console.log("toggle 1 2 3");
      this.showAddWishList = !this.showAddWishList;
      console.log(this.showAddWishList);
    },
    deleteAll() {
      console.log("Delete all 2");
      this.wishlist = [];
    },
    addWish(wish) {
      console.log(wish);
      this.wishlist = [...this.wishlist, wish];
    },
    deleteItem(id) {
      console.log(id, "app");
      this.wishlist = this.wishlist.filter((item) => item.id !== id);
    },
    toggleUrgent(id) {
      console.log("Urgent toggle", id);
      this.wishlist = this.wishlist.map((item) =>
        item.id === id ? { ...item, urgent: !item.urgent } : item
      ); //TODO: Doubt
    },
  },
  created() {
    this.wishlist = [
      { id: 1, wish: "Buy 100 cars", urgent: true },
      { id: 2, wish: "Buy 10 aloos", urgent: false },
      { id: 3, wish: "Get toffees", urgent: false },
      { id: 4, wish: "Get coffee", urgent: false },
      { id: 5, wish: "Get soap", urgent: true },
    ];
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
</style>
