<template>
  <div class="row mt-4">
    <div class="col-3" v-bind:key="item.id" v-for="item in items">
      <ListItems
        v-bind:id="item.id"
        v-bind:title="item.title"
        v-bind:item="item"
        v-on:del-item="$emit('del-item', item.id)"
        v-bind:items="items"
      />
    </div>
  </div>
</template>

<script>
import ListItems from "./ListItems.vue";
export default {
  name: "List",
  components: {
    ListItems,
  },
  props: ["items"],
};
</script>
<style scoped>
.shadow {
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
</style>
