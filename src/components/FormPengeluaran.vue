<template>
  <div class="container">
    <div>
      <form @submit.prevent="tambah">
        <div>
          <label>Pengeluaran</label>
          <input v-model="pengeluaran" type="number" class="form-control mt-1" id="pengeluaran" />
        </div>
        <div class="mt-4">
          <label>Keterangan</label>
          <input v-model="keterangan" type="text" class="form-control" id="keterangan" />
        </div>

        <div class="mt-4">
            <button class="btn btn-danger">Tambah</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            pengeluaran : null,
            keterangan : null,
        }
    },
    methods:{
        tambah(){
            this.$emit('entri-pengeluaran', {
                nominal : this.pengeluaran,
                keterangan : this.keterangan,
            });

            this.pengeluaran = null,
            this.keterangan = null,
            document.getElementById('pengeluaran').focus();
        }
    }
}
</script>
