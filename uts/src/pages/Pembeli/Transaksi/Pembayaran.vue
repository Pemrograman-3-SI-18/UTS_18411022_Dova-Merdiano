<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
  <q-page padding class="items-center-justify-center bg-grey-3">
    <q-card flat class="bg-white q-pa-md">
      <span class="text-h5 text-weight-light q-pa-md">
        <span class="text-blue-grey-14">Pembayaran</span>
      </span>
      <div class="q-pa-md">
        <q-form
          class="q-gutter-md"
        >
          <q-input
            label="Kode Transaksi"
            lazy-rules
            color="teal"
            v-model="kodetr"
            :rules="[
           val => val !== null && val !== '' || 'Kode Transaksi Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="arrow_back"/>
            </template>
          </q-input>

          <q-input
            label="User Name"
            lazy-rules
            color="teal"
            v-model="user"
            :rules="[
           val => val !== null && val !== '' || 'User Name Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="accessibility"/>
            </template>
          </q-input>

          <q-input
            label="Alamat Penerima"
            lazy-rules
            color="teal"
            v-model="alamat"
            :rules="[
           val => val !== null && val !== '' || 'Alamat Penerima Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="my_location"/>
            </template>
          </q-input>

          <q-input
            label="Nomor Telepon"
            lazy-rules
            color="teal"
            v-model="notelp"
            :rules="[
           val => val !== null && val !== '' || 'Nomor Telepon Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="call"/>
            </template>
          </q-input>

          <q-input
            label="Kode Virtual Pembayaran"
            lazy-rules
            color="teal"
            v-model="virtual"
            :rules="[
           val => val !== null && val !== '' || 'Konfirmasi Admin'
           ]">
            <template v-slot:append>
              <q-icon name="verified_user"/>
            </template>
          </q-input>

          <div>
            <q-btn
              unelevated
              icon="local_shipping"
              label="Bayar Transaksi"
              style="height: 50px"
              color="teal-6"
              to="/pembeli/transaksi"/>
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
      kodetr: null,
      user: null,
      alamat: null,
      notelp: null,
      virtual: null
    }
  }
}
</script>

<style scoped>

</style>
