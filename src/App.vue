<template>
  <Header title="Convert to" />
  <div class="container">
    <div class="row">
      <Form v-on:nuevo-item="HandleSubmit" />
      <div class="col-lg-12">
        <List v-bind:items="items" v-on:del-item="deleteItem" />
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import List from "./components/List.vue";
import Form from "./components/Form.vue";

export default {
  name: "App",
  data() {
    return {
      items: [],
    };
  },
  components: {
    Header,
    List,
    Form,
  },
  methods: {
    HandleSubmit(agregar) {
      this.items = [...this.items, agregar];
    },
    deleteItem(id) {
      this.items = this.items.filter((item) => item.id !== id);
    },
  },
};
</script>
<style>
body {
  background-color: #eee;
}
</style>
