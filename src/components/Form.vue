<template>
  <div class="col-lg-6 pt-4">
    <form @submit="HandleSubmit" class="bg-light">
      <h3 class="text-center">Calculadora para Recibir <span class="text-success font-weight-bold">pagos</span></h3>
      <div class="form-group">
          <label for="" class="bold">Para recibir</label>
          <input required type="number" v-model.number="cantidad" placeholder="cantidad" name="cantidad" class="form-control">
      </div>
      <div class="form-group">
        <label for="">Hay que enviar</label>
        <input type="number" class="form-control" disabled :placeholder="[[cantidad + (cantidad * 5) / 100]]">
      </div>
      <div class="form-group">
        <label for="">Comision</label>
        <input type="number" class="form-control" disabled :placeholder="[[(cantidad * 5) / 100]]">
      </div>
      <div class="form-group">
          <button class="btn btn-block btn-success">
              Agregar
          </button>
      </div>
    </form>
  </div>
  <div class="col-lg-6 pt-4">
    <Convert :cantidad="cantidad" />
  </div>
</template>
<script>
import Convert from './Convert.vue'
export default {
  name: "Form",
  data() {
    return {
      cantidad: 0
    }
  },
  methods: {
    HandleSubmit(e) {
        e.preventDefault()
      const agregar = {
        id:Date.now(),
        cantidad: this.cantidad,
      }
      this.$emit('nuevo-item', agregar);
      this.cantidad = 0;
    }
  },
  components: {
      Convert,
  }
}
</script>
<style scoped>
form {
  border: 2px solid #5679DE;
  padding: 3rem;
  border-radius: 1rem;
  min-height: 60vh;
}
</style>