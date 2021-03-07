<template>
  <div :key="item.id" v-for="item in wishlist">
    <!-- <h3>{{ item.wish }}</h3> -->
    <Item
      @delete-item="$emit('delete-item', item.id)"
      @toggle-urgent="$emit('toggle-urgent', item.id)"
      :item="item"
    />
  </div>
</template>

<script>
import Item from "./Item";
export default {
  name: "WishList",
  props: {
    wishlist: Array,
  },
  components: {
    Item,
  },
  emits: ["delete-item", "toggle-urgent"],
};
</script>
<style scoped>
* {
  box-sizing: border-box;
}
.column {
  float: left;
  width: 50%;
  padding: 10px;
}
.row:after {
  content: "";
  display: table;
  clear: both;
}
</style>