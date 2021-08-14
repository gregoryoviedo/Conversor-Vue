<template>
<table class="bg-light table mt-4">
  <tbody>
    <tr v-bind:key="item.id" v-for="item in items">
      <ListItems v-bind:id="item.id" v-bind:title="item.title"
      v-bind:item="item" v-on:del-item="$emit('del-item', item.id)"
      v-bind:items="items"/>
    </tr>
  </tbody>
</table>
</template>

<script>
import ListItems from './ListItems.vue';
export default {
  name: "List",
  components: {
    ListItems
  },
  props: ["items"]
}
</script>
<style scoped>
table {
  border: 2px solid #5679DE;
}
</style>