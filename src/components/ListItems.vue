<template>
  <div class="card text-dark bg-light mb-3">
    <div class="card-header"></div>
    <div class="card-body">
      <span>Receive {{ item.cantidad }}</span>

      <p class="card-text">
        Send {{ item.cantidad + (item.cantidad * 5) / 100 }}
      </p>
      <p class="card-text">Commission {{ (item.cantidad * 5) / 100 }}</p>
      <button
        @click="$emit('del-item', item.id)"
        class="btn btn-danger btn-sm float-right"
      >
        Delete
        <i class="fas fa-trash-alt"></i>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ListItems",
  props: ["item", "items", "cantidad", "id"],
};
</script>
<style scoped>
.dolar {
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
</style>
