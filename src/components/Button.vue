<template>
  <button @click="onClick()" class="button">{{ label }}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    label: String,
  },
  methods: {
    onClick() {
      if (this.label == "Delete All Items") {
        this.$emit("delete-all");
      } else if (this.label == "Add Random Item") {
        this.$emit("add-random");
      } else {
        this.$emit("show-add-task");
      }
    },
  },
};
</script>

<style scoped>
.button {
  background-color: #b2ddec; /* Green */
  border: none;
  color: rgb(61, 8, 8);
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}
</style>