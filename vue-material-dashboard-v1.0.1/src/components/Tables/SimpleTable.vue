<template>
  <div>
    <md-table v-model="mdata">
      <md-table-row slot="md-table-row" slot-scope=" item ">
        <md-table-cell md-label="Contrato">{{ item.item.nucontrato }}</md-table-cell>
        <md-table-cell md-label="Movimiento">{{ item.item.tipopago.detalle }}</md-table-cell>
        <md-table-cell md-label="Boleta">{{ item.item.comprobanteid }}</md-table-cell>
        <md-table-cell md-label="Fecha"> {{ item.item.fechaimp | fecha}} </md-table-cell>
        <md-table-cell md-label="Hora">{{ item.item.horegistro }}</md-table-cell>
        <md-table-cell md-label="SubTotal">{{ item.item.subtotal }}</md-table-cell>
        <md-table-cell md-label="IGV">{{ item.item.toigv }}</md-table-cell>
        <md-table-cell md-label="Total">{{ item.item.valortotal }}</md-table-cell>
        <md-table-cell md-label="Doc.">
          <md-menu md-direction="top-end">
            <md-button md-menu-trigger>Donwnload</md-button>

            <md-menu-content>

              <md-menu-item>Ticket</md-menu-item>
              <md-menu-item>Boleta</md-menu-item>
              <md-menu-item>Hoja</md-menu-item>
            </md-menu-content>
          </md-menu>

        </md-table-cell>
        <!--<md-table-cell md-label="Total">{{ item.item.topagado }}</md-table-cell>
        <md-table-cell md-label="Salary">{{ item }}</md-table-cell>-->
      </md-table-row>
    </md-table>

  </div>
</template>

<script>

  var moment = require('moment');
  const fechaFilter = function(value) {
      return moment(value).format('DD/MM/YYYY');
    }
export default {

  name: 'simple-table',
  props: ['mdata'],
  filters: {
    fecha: fechaFilter,
  },
  //{tableHeaderColor: {type: String,default: ''}}
  data () {
    return {
      selected: [],
      users: [
        {
          name: 'Dakota Rice',
          salary: '$36,738',
          country: 'Niger',
          city: 'Oud-Turnhout'
        },
        {
          name: 'Minerva Hooper',
          salary: '$23,738',
          country: 'Curaçao',
          city: 'Sinaai-Waas'
        },
        {
          name: 'Sage Rodriguez',
          salary: '$56,142',
          country: 'Netherlands',
          city: 'Overland Park'
        },
        {
          name: 'Philip Chaney',
          salary: '$38,735',
          country: 'Korea, South',
          city: 'Gloucester'
        },
        {
          name: 'Doris Greene',
          salary: '$63,542',
          country: 'Malawi',
          city: 'Feldkirchen in Kārnten'
        },
        {
          name: 'Mason Porter',
          salary: '$78,615',
          country: 'Chile',
          city: 'Gloucester'
        }
      ]
    }
  }
}
</script>
