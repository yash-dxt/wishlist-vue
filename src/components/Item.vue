<template>
  <div
    @dblclick="$emit('toggle-urgent', item.id)"
    :class="['div', item.urgent ? 'urgent' : '']"
  >
    <h3>
      {{ item.wish }}
      <h1><i @click="onDelete(item.id)" class="fas fa-times"></i></h1>
    </h3>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: {
    item: Object,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-item", id);
      console.log(id + "Aloo");
    },
  },
};
</script>

<style scoped>
.div {
  padding: 15px;
  margin: 10px;
  background-color: #b2ddec;
  color: #333333;
}
.div.urgent {
  border-left-color: blue;
  background-color: red;
}
.div h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.fas {
  color: black;
  width: 50px;
  /* height: 50px; */
}
</style>