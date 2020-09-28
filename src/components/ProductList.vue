<template>
  <div id="list">
    <p v-if="products.length == 0">Ürün Listesi Boş.</p>
    <table v-else class="table">
      <thead>
        <tr>
          <th>Id</th>
          <th>Name</th>
          <th>E-mail</th>
          <th>Body</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product.id">
          <td v-if="updateId === product.id">
            <input
              v-model="product.id"
              type="text"
              class="form-control"
              id="id"
            />
          </td>
          <td v-else>
            {{ product.id }}
          </td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.name"
              type="text"
              class="form-control"
              id="name"
            />
          </td>
          <td v-else>
            {{ product.name }}
          </td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.email"
              type="text"
              class="form-control"
              id="email"
            />
          </td>
          <td v-else>
            {{ product.email }}
          </td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.Body"
              type="text"
              class="form-control"
              id="body"
            />
          </td>
          <td v-else>
            {{ product.body }}
          </td>
          <td v-if="updateId !== product.id">
            <button
              class="btn btn-sm btn-primary"
              @click="handleUpdate(product)"
            >
              Güncelle
            </button>
            <button
              class="btn btn-sm btn-danger"
              @click="handleDelete(product)"
            >
              Sil
            </button>
          </td>
          <td v-else>
            <button class="btn btn-sm btn-primary" @click="handleSave(product)">
              Kaydet
            </button>
            <button class="btn btn-sm btn-danger" @click="updateId = null">
              İptal
            </button>
          </td>
        </tr>
      </tbody>
    </table>
    {{ products.length }}
  </div>
</template>
<script>
export default {
  name: "product-list",
  data() {
    return { updateId: null };
  },
  props: {
    products: Array,
  },
  methods: {
    handleDelete(product) {
      this.$emit("delete:product", product);
    },
    handleUpdate(product) {
      this.updateId = product.id;
    },
    handleSave(product) {
      this.$emit("update:product", product);
      this.updateId = null;
    },
  },
};
</script>
<style scoped>
#list {
  margin: 100px;
}
</style>