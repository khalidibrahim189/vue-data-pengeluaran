<template>
  <div class="container">
    <Header title="Data Pengeluaran" />
    <FormPengeluaran @entri-pengeluaran="entriPengeluaran($event)" />

    <ListPengeluaran v-if="tampilData" :dataPengeluaran="dataPengeluaran" />

    <h4 class="mt-2">Total Uang Keluar : {{ totalPengeluaran }}</h4>

    <p v-if="warning" class="warning text-danger">Pengeluaran terlalu banyak!!</p>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import ListPengeluaran from "./components/ListPengeluaran.vue";
import FormPengeluaran from "./components/FormPengeluaran.vue";
export default {
  name: "App",
  components: {
    Header,
    ListPengeluaran,
    FormPengeluaran,
  },

  data() {
    return {
      dataPengeluaran: [
        // {
        //   nominal: 10000,
        //   keterangan: "Bensin",
        // },
        // {
        //   nominal: 20000,
        //   keterangan: "Kuota",
        // },
        // {
        //   nominal: 30000,
        //   keterangan: "Makan",
        // },
      ],

      warning: false,
    };
  },

  methods: {
    entriPengeluaran(event) {
      this.dataPengeluaran.push(event);
    },
  },

  computed: {
    tampilData: function() {
      return this.dataPengeluaran.length > 0;
    },
    totalPengeluaran : function(){
      return this.dataPengeluaran.reduce((accum, item) => accum + parseInt(item.nominal), 0);
    }
  },

  watch:{
    totalPengeluaran: function(val){
      if(val > 100000){
        this.warning = true;
      }
    }
  }
};
</script>

<style></style>
