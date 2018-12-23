<template>
  <div class="">
    <v-card flat style="background: none !important">
      <v-layout row wrap>
        <v-flex xs12 sm3>
          <div class="ticket-menu--scroll">
            <v-card-text>
              
              <v-btn  color="white"   small block  >
                  <span>Compose new ticket </span> 
                </v-btn>
        
              <v-list style="background: none !important">  
              <v-subheader> QUEUES </v-subheader>          
                <v-list-tile v-for="menu in menus" @click="">
                    <v-list-tile-action>
                      <v-icon >{{ menu.icon }}</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>{{ menu.title }}</v-list-tile-title>
                    </v-list-tile-content>
                    <v-list-tile-action>
                   {{ menu.badge}}
                  </v-list-tile-action>
                  </v-list-tile>

                  

                   <v-subheader> CATEGORIES </v-subheader>

                   <v-list-tile v-for="cat in categories" @click="">
                    <v-list-tile-action>
                      <v-icon >{{ cat.icon }}</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                      <v-list-tile-title>{{ cat.title }}</v-list-tile-title>
                    </v-list-tile-content>
                  </v-list-tile>
              </v-list>
            </v-card-text>
          </div>  
         </v-flex>
         <v-flex xs12 sm9>
            <div class="container">
              <v-toolbar card  color="white" class="pa-0">
               
                 <v-text-field class="pt-0"
                            prepend-icon="search"
                            placeholder=" Search tickets"                           
                           
                            hide-details
                          ></v-text-field>
                <v-spacer></v-spacer>          
                           <v-autocomplete prepend-icon="filter_list" placeholder="Category" ></v-autocomplete>
                <v-spacer></v-spacer>
                <v-btn icon>
                  <v-icon>apps</v-icon>
                </v-btn>
                <v-btn icon>
                  <v-icon>more_vert</v-icon>
                </v-btn>
              </v-toolbar>
              <v-divider></v-divider>
            <v-data-table
                   :items="rows"
                  class="elevation-1"
                  item-key="id"
                  hide-actions
                  hide-headers
                >
                  <template slot="items" slot-scope="props">
                    <tr class="mb-1">
                      <td width="50px;">
                        <v-checkbox
                         
                          primary
                          hide-details
                        ></v-checkbox>
                      </td>
                      <td width="50px;" >
                          <v-avatar size="40">
                            <img :src="img_url +'uploads/contacts/'+ props.item.avatar " alt="avatar">
                          </v-avatar>
                      </td>
                      <td class="pt-2">
                          
                          <h3 class="mt-2 mb-2"> {{ props.item.title }} </h3>
                         
                          <p><b>From :  {{ props.item.customer }} </b>  Created : {{ props.item.date }} </p> 

                      </td>
                      <td  class="hidden-sm-and-down">
                        <v-icon>forum</v-icon> <b>4</b>
                      </td>
                      <td> <b> {{ props.item.priority }} </b> </td>
                     
                     
                    </tr>  
                    </template>

                </v-data-table> 
            </div>

         </v-flex>

      </v-layout>
    </v-card>  
  </div>
</template>
<script>
import axios from 'axios'
import {store} from '../../store'
import moment from 'moment'
import PulseLoader from 'vue-spinner/src/PulseLoader.vue'
  export default {
    $_veeValidate: {
      validator: 'new'
    },
    name: 'Sv_CRUD',
    components: {
      PulseLoader
    },    
     data () {
        return {
        /* END Dinamic Data From CRUDENGINE */        
        //status_active: true   
          baseUrl : store.state.baseUrl +'helpdesk/ticket',
          menus :[
            { title : 'All Tickets' , badge : '24' ,icon :'mail'},
            { title : 'Unresponed', badge : '5' ,icon :'portrait'},
            { title : 'Due Today', badge : '1' ,icon :'access_time'},
            { title : 'My Tickets', badge : '14' ,icon :'loop'}
          ],
           categories :[
            { title : 'Billing & Returs' , badge : '24' ,icon :'turned_in_not'},
            { title : 'Marketing', badge : '5' ,icon :'turned_in_not'},
            { title : 'Sales', badge : '1' ,icon :'turned_in_not'},
            { title : 'Supports', badge : '14' ,icon :'turned_in_not'}
          ],
          rows : [
            { id:'1', title : 'Refund Please' , customer :'Iwan K' , avatar :'1.jpg' ,  date : '30 Minutes ago' , status :'respond' , priority : 'Low'},
            { id:'2', title : 'My Credit Card has been changed twice' , customer :'Alfredo' , avatar :'2.jpg' ,  date : 'a few seconds ago' ,status : 'new' , priority :'High' , },
            { id:'2', title : 'My Coupon is not working' , customer :'Alfredo' , avatar :'3.jpg' ,  date : '2 Minutes ago' ,status : 'replied' , priority :'High'},
            { id:'2', title : 'Missing Link' , customer :'Alfredo' , avatar :'4.jpg' ,  date : '30 Minutes ago' ,status : 'Open' , priority :'High'},
            { id:'2', title : 'Upload error both image or file ' , customer :'Alfredo' , avatar :'5.jpg' ,  date : '1 days ago' ,status : 'replied' , priority :'High'},
            { id:'1', title : 'Refund Please' , customer :'Iwan K' , avatar :'1.jpg' ,  date : '30 Minutes ago' , status :'respond' , priority : 'Low'},
            { id:'2', title : 'My Credit Card has been changed twice' , customer :'Alfredo' , avatar :'2.jpg' ,  date : 'a few seconds ago' ,status : 'new' , priority :'High' , },
            { id:'2', title : 'My Coupon is not working' , customer :'Alfredo' , avatar :'3.jpg' ,  date : '2 Minutes ago' ,status : 'replied' , priority :'High'},
            { id:'2', title : 'Missing Link' , customer :'Alfredo' , avatar :'4.jpg' ,  date : '30 Minutes ago' ,status : 'Open' , priority :'High'},
            { id:'2', title : 'Upload error both image or file ' , customer :'Alfredo' , avatar :'5.jpg' ,  date : '1 days ago' ,status : 'replied' , priority :'High'}

          ],
           img_url : store.state.baseUrl,
        
        }
    },    
    mounted: function () 
    {
       
          
    },
    methods : {
     


    }

}
</script>
<style>
 .ticket-menu--scroll {
      height: calc(100vh - 65px);
      overflow: auto
  }
</style>