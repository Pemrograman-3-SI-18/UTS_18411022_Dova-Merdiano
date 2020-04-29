<template>
  <q-page >
    <div class="q-pa-md">
      <q-table
        title="Treats"
        :data="data"
        :columns="columns"
        row-key="id"
        :filter="filter"
        :loading="loading"
      >

        <template v-slot:top>
          <span class="text-h5 text-weight-light q-pa-md">
            <span class="text-blue-grey-14">Data Transaksi</span>
          </span>
          <q-space />
          <q-input borderless dense debounce="300" color="primary" v-model="filter">
            <template v-slot:append>
              <q-icon name="search" />
            </template>
          </q-input>
        </template>

      </q-table>
    </div>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      loading: false,
      filter: '',
      rowCount: 10,
      columns: [
        {
          name: 'desc',
          required: true,
          label: 'Kode Transaksi',
          align: 'left',
          field: row => row.kodetransaksi,
          format: val => `${val}`,
          sortable: true
        },
        { name: 'user', align: 'center', label: 'User Name', field: 'user', sortable: true },
        { name: 'alamat', align: 'center', label: 'Alamat Antar', field: 'alamat' },
        { name: 'notelp', align: 'center', label: 'No Telepon', field: 'notelp' },
        { name: 'merk', align: 'center', label: 'Merk Sepeda', field: 'merk', sortable: true },
        { name: 'harga', align: 'center', label: 'Harga Sepeda', field: 'harga' },
        { name: 'jumlahbeli', align: 'center', label: 'Jumlah Beli', field: 'jumlahbeli' },
        { name: 'total', align: 'center', label: 'Total', field: 'total' },
        { name: 'bayar', align: 'center', label: 'Status Pembayaran', field: 'bayar' },
        { name: 'kirim', align: 'center', label: 'Status Pengirman', field: 'kirim' }
      ],

      data: [
        {
          kodetransaksi: 'T-711-101',
          user: 'Dova Merdiano',
          alamat: 'Way Kanan',
          notelp: '081377972201',
          merk: 'Sepeda Lipat Amadeus FDB20 Steel',
          harga: 'Rp2.759.400',
          jumlahbeli: '1',
          total: 'Rp2.759.400',
          bayar: 'Succes',
          kirim: 'Sudah Di Terima'
        },

        {
          kodetransaksi: 'T-344-301',
          user: 'Angga Saputra',
          alamat: 'Baradatu',
          notelp: '082298970012',
          merk: 'Sepeda MTB Vivacycle Prompt Curve 27.5"',
          harga: 'RP.1.899.000',
          jumlahbeli: '1',
          total: 'RP.1.899.000',
          bayar: 'Succes',
          kirim: 'Sudah Di Terima'
        },

        {
          kodetransaksi: 'T-323-303',
          user: 'Dova Merdiano',
          alamat: 'Way Kanan',
          notelp: '081377972201',
          merk: 'SEPEDA 27.5 MTB ODESSY SIBERIA NEW',
          harga: 'Rp1.250.000',
          jumlahbeli: '2',
          total: 'Rp2.500.000',
          bayar: 'Succes',
          kirim: 'Dalam Perjalanan'
        },

        {
          kodetransaksi: 'T-993-866',
          user: 'Sateria',
          alamat: 'Gunung Kemuning',
          notelp: '08139943561',
          merk: 'Sepeda London Taxi Road Bike 700C',
          harga: 'Rp2.910.000',
          jumlahbeli: '5',
          total: 'Rp14.550.000',
          bayar: 'Belum Bayar',
          kirim: 'Belum Dikirim'
        }
      ]
    }
  },

  methods: {
    // emulate fetching data from server
    addRow () {
      this.loading = true
      setTimeout(() => {
        const
          index = Math.floor(Math.random() * (this.data.length + 1)),
          row = this.original[Math.floor(Math.random() * this.original.length)]
        if (this.data.length === 0) {
          this.rowCount = 0
        }
        row.id = ++this.rowCount
        const addRow = { ...row } // extend({}, row, { name: `${row.name} (${row.__count})` })
        this.data = [...this.data.slice(0, index), addRow, ...this.data.slice(index)]
        this.loading = false
      }, 500)
    },

    removeRow () {
      this.loading = true
      setTimeout(() => {
        const index = Math.floor(Math.random() * this.data.length)
        this.data = [...this.data.slice(0, index), ...this.data.slice(index + 1)]
        this.loading = false
      }, 500)
    }
  }
}
</script>
