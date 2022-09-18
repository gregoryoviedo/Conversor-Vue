<template>
  <form class="bg-light">
    <h3>
      Convert the to
      <span class="text-success font-weight-bold">currency</span> a another
    </h3>
    <div class="form-group">
      <label for="">Choose your preferred currency</label>
      <select class="form-control" @change="convertir" v-model="moneda">
        <option selected disabled value="">Selecciona tu moneda</option>
        <option :value="dato" v-for="(dato, key) in datos" :key="dato.id">
          {{ key }}
        </option>
      </select>
    </div>
    <div class="form-group row">
      <label for="" class="col-sm-2 col-form-label">Receive</label>
      <div class="form-group col-sm-10">
        <input
          required
          type="number"
          :placeholder="[[cantidad * moneda]]"
          class="form-control"
          disabled
        />
      </div>
    </div>
    <div class="form-group row">
      <label for="" class="col-sm-2 col-form-label">Send</label>
      <div class="form-group col-sm-10">
        <input
          type="number"
          class="form-control"
          disabled
          :placeholder="[[(cantidad + (cantidad * 5) / 100) * moneda]]"
        />
      </div>
    </div>
    <div class="form-group row">
      <label for="" class="col-sm-2 col-form-label">Commission</label>
      <div class="form-group col-sm-10">
        <input
          type="number"
          class="form-control"
          disabled
          :placeholder="[[((cantidad * 5) / 100) * moneda]]"
        />
      </div>
    </div>
    <div class="form-group">
      <p v-if="moneda > 1" class="float-right font-weight-bold">
        Tasa acutal del dia
        <span class="badge badge-secondary taza__actual"> {{ moneda }}</span>
      </p>
    </div>
  </form>
</template>
<script>
import axios from "axios";

export default {
  name: "Convert",
  data() {
    return {
      datos: {},
      moneda: 0,
    };
  },
  mounted() {
    this.getDatos();
  },
  methods: {
    getDatos() {
      axios
        .get(
          `http://data.fixer.io/api/latest?access_key=a7bc3ff8a535f63a8dda458a58a40e91`
        )
        .then((respuesta) => {
          this.datos = respuesta.data.rates;
        })
        .catch((e) => console.log(e));
    },
    convertir() {
      this.result = this.moneda;
    },
  },
  props: {
    cantidad: Number,
  },
};
</script>
<style scoped>
.taza__actual {
  font-size: 1.5rem;
}
</style>
