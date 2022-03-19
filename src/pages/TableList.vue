<template>
  <div class="content">
    <div class="md-layout">
      
      

      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100"
      >
      <md-button class="md-success">Add Job</md-button>
      <stats-card data-background-color="blue" v-for="item in list" v-bind:key="item.id">
          <template slot="header">
            <md-icon>work_outline</md-icon>
          </template>

          <template slot="content">
            <h3 class="title">{{item.jobName}}</h3>
            <p class="category">{{item.jobPosition}}</p>
            <md-button class="md-success">Add Job</md-button>
            
          </template>

          <template slot="footer">
            <div class="stats">
              <md-icon>account_balance_wallet</md-icon>
              Rp. {{item.jobSalary}}
            </div>
          </template>
        </stats-card>
      </div>
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100"
      >
        <md-card>
          <md-card-header data-background-color="green">
            <h4 class="title">Simple Table</h4>
            <p class="category">Here is a subtitle for this table</p>
          </md-card-header>
          <md-card-content>
            <simple-table table-header-color="green"></simple-table>
          </md-card-content>
        </md-card>
      </div>

      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-100"
      >
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
import { SimpleTable, OrderedTable, StatsCard } from "@/components";
import axios from 'axios'

export default {
  components: {
    OrderedTable,
    SimpleTable,
    StatsCard,
  },
  data() {
    return {

      list:[],
      
      
    };
  },
   mounted(){
    
    axios.get(`http://54.255.4.75:9091/api/v1/jobs/5`)
    .then((resp)=>{
      this.list=resp.data
      console.log(resp)
      
      
    })
    
  }
};
</script>