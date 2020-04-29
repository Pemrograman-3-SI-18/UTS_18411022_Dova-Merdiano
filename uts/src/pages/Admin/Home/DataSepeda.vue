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
          <q-btn color="teal" :disable="loading" label="Tambah Data Sepeda" to="/admin/inputdata" />
          <!-- <q-btn class="q-ml-sm" color="primary" :disable="loading" label="Remove row" @click="removeRow" /> -->
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
          label: 'Kode Sepeda',
          align: 'left',
          field: row => row.kodesepeda,
          format: val => `${val}`,
          sortable: true
        },
        { name: 'merk', align: 'center', label: 'Merk Sepeda', field: 'merk', sortable: true },
        { name: 'stok', align: 'center', label: 'Jumlah Stok', field: 'stok', sortable: true },
        { name: 'harga', align: 'center', label: 'Harga Sepeda', field: 'harga' }
      ],

      data: [
        {
          kodesepeda: 'K0001',
          merk: 'SEPEDA 27.5 MTB ODESSY SIBERIA NEW',
          stok: '202',
          harga: 'Rp1.250.000'
        },

        {
          kodesepeda: 'K0002',
          merk: 'Sepeda London Taxi Road Bike 700C',
          stok: '50',
          harga: 'Rp2.910.000'
        },

        {
          kodesepeda: 'K0003',
          merk: 'Sepeda MTB Vivacycle Prompt Curve 27.5"',
          stok: '60',
          harga: 'RP.1.899.000'
        },

        {
          kodesepeda: 'K0004',
          merk: 'Sepeda Lipat Amadeus FDB20 Steel',
          stok: '10',
          harga: 'Rp2.759.400'
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
