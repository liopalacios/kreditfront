<template>
  <div class="content">
    <div class="md-layout">
      <div class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100">
        <md-card>
          <md-card-header data-background-color="green">
            <h4 class="title">Simple Table</h4>
            <p class="category">Here is a subtitle for this table</p>
          </md-card-header>
          <md-card-content>
            <simple-table table-header-color="green" :mdata="listclients"></simple-table>
          </md-card-content>
        </md-card>
      </div>

{{cliente}}
      <div class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100">
        <md-card class="md-card-plain">
          <md-card-header data-background-color="green">
            <h4 class="title">Table on Plain Background</h4>
            <p class="category">Here is a subtitle for this table</p>
          </md-card-header>
          <md-card-content>
            <ordered-table></ordered-table>
          </md-card-content>
        </md-card>
      </div>
    </div>
  </div>
</template>

<script>
import {
  SimpleTable,
  OrderedTable
} from '@/components'
import axios from 'axios'

export default{
  data() {
    return {
      listclients:[],
      cliente:[],
    }
  },
  mounted(){

      axios.get(`http://localhost:8080/api/revisaBoleta?clienteid=006141`)
        .then(response => {
          // JSON responses are automatically parsed.
          console.log(response.data)
          this.loadBoletas()
          this.loadclient()
        })
        .catch(e => {
          this.listclients=e
          this.loadBoletas()
          this.loadclient()
        })


  },
  components: {
    OrderedTable,
    SimpleTable
  },
  methods:{
    loadBoletas(){
      axios.get(`http://localhost:8080/api/pagosBoleta?clienteid=006141`)
        .then(response => {
          // JSON responses are automatically parsed.
          this.listclients = response.data
        })
        .catch(e => {
          this.listclients=e
        })
    },
    loadclient(){
      axios.get(`http://localhost:8080/api/cliente?clienteid=006141`)
        .then(response => {
          // JSON responses are automatically parsed.
          this.cliente = response.data
        })
        .catch(e => {
          this.cliente=e
        })
    }
  }
}
</script>
