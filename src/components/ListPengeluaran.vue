<template>
  <div class="container">
    <table class="table table-striped table-bordered mt-5">
      <thead class="">
        <tr>
          <th scope="col">Nominal</th>
          <th scope="col">Keterangan</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for=" (pengeluaran, index) in dataPengeluaran" :key="index"> 
          <td>
              {{ pengeluaran.nominal }}
          </td>

          <td>
              {{ pengeluaran.keterangan }}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    dataPengeluaran: Array,
  },
};
</script>
