<template>
  <td>
    <span class="font-weight-bold">Recibir</span> {{item.cantidad}}
  </td>
  <td>
     <span class="font-weight-bold">Enviar</span> {{item.cantidad + (item.cantidad * 5) / 100}}
  </td>
  <td>
     <span class="font-weight-bold">Comision</span> {{ (item.cantidad * 5) / 100}} 
  </td>
  <td>
    <button @click="$emit('del-item', item.id)" class="btn btn-danger btn-sm float right"><i class="fas fa-trash-alt"></i></button>
  </td>
</template>

<script>
export default {
  name: "ListItems",
  props: ["item", "items", "cantidad", "id"],
};
</script>