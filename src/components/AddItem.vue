<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Wish</label>
      <input
        type="text"
        v-model="text"
        name="text"
        placeholder="Name of Wish"
      />
    </div>

    <div class="form-control form-control-check">
      <label>Urgent</label>
      <input type="checkbox" v-model="urgent" name="urgent" />
    </div>
    <input type="submit" value="Save Wish" class="btn btn-block" />
  </form>
</template>
<script>
export default {
  name: "AddItem",
  data() {
    return {
      text: "",
      urgent: false,
    };
  },
  methods: {
    onSubmit(e) {
      console.log("huehehahahh");
      e.preventDefault();
      if (this.text === "") {
        alert("Please add a wish");
        return;
      }
      const wish = {
        id: Math.floor(Math.random() * 100000),
        wish: this.text,
        urgent: this.urgent,
      };
      console.log(wish);
      this.$emit("add-wish", wish);
      this.text = "";
      this.urgent = false;
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>