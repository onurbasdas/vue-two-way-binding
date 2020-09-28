<template>
  <div id="addForm">
    <form @submit.prevent="handleAdd">
      <div class="form-group">
        <label for="id">Id</label>
        <input v-model="product.id" type="text" class="form-control" id="id" />
      </div>
      <div class="form-group">
        <label for="name">Name</label>
        <input
          v-model="product.name" 
          type="text"
          class="form-control"
          id="name"
        />
      </div>
      <div class="form-group">
        <label for="email">E-mail</label>
        <input
          v-model="product.email"
          type="text"
          class="form-control"
          id="email"
        />
      </div>
      <div class="form-group">
        <label for="body">Body</label>
        <input
          v-model="product.body"
          type="text"
          class="form-control"
          id="body"
        />
      </div>

      <button type="submit" class="btn btn-sm btn-success">Ekle</button>
    </form>
  </div>
</template>
<script>
export default {
  name: "product-add",
  data() {
    return {
      product: {
        id: "",
        name: "",
        email: "",
        body: "",
      },
    };
  },
  methods: {
    handleAdd() {
      this.$emit("add:product", this.product);
    },
  },
};
</script>
<style scoped>
#addForm {
  margin: 100px;
}
</style>