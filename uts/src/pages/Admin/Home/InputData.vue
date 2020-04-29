<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
  <q-page padding class="items-center-justify-center bg-grey-3">
    <q-card flat class="bg-white q-pa-md">
      <span class="text-h5 text-weight-light q-pa-md">
        <span class="text-blue-grey-14">Tambah Data Sepeda</span>
      </span>
      <div class="q-pa-md">
        <q-form
          class="q-gutter-md"
        >
          <q-input
            label="Kode Sepeda"
            lazy-rules
            color="teal"
            v-model="kode"
            :rules="[
           val => val !== null && val !== '' || 'Kode Sepeda Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="directions_bike"/>
            </template>
          </q-input>

          <q-input
            label="Merk Sepeda"
            lazy-rules
            color="teal"
            v-model="merk"
            :rules="[
           val => val !== null && val !== '' || 'Merk Sepeda Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="local_activity"/>
            </template>
          </q-input>

          <q-input
            label="Jumlah Stok"
            lazy-rules
            color="teal"
            v-model="stok"
            :rules="[
           val => val !== null && val !== '' || 'Jumlah Stok Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="move_to_inbox"/>
            </template>
          </q-input>

          <q-input
            label="Harga Sepeda"
            lazy-rules
            color="teal"
            v-model="harga"
            :rules="[
           val => val !== null && val !== '' || 'Harga Sepeda Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="attach_money"/>
            </template>
          </q-input>

          <div>
            <q-btn
              unelevated
              icon="add"
              label="Tambah Data Sepeda"
              style="height: 50px"
              color="teal-6"
              to="/admin"/>
          </div>
        </q-form>
      </div>
    </q-card>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      kode: null,
      merk: null,
      stok: null,
      harga: null
    }
  }
}
</script>

<style scoped>

</style>
