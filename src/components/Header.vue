<template>
  <div>
    <ul>
      <li>WishList</li>
      <li>
        <Button @delete-all="$emit('delete-all')" label="Delete All Items" />
      </li>
      <li>
        <Button @add-random="$emit('add-random')" label="Add Random Item" />
      </li>
      <li>
        <Button @show-add-task="$emit('show-add-task')" label="Add New Task" />
      </li>
    </ul>
  </div>
</template>

<script>
import Button from "./Button";

export default {
  name: "Header",
  components: {
    Button,
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #333333;
}

li {
  float: left;
}

li {
  display: block;
  color: white;
  text-align: center;
  padding: 16px;
  text-decoration: none;
}
</style>