<template>
  <div>
         <v-tabs
              
              color="white"
              icons-and-text
              class="mb-2"
              centered
              v-model="selected_tab"
            >
             <v-tabs-slider color="indigo"></v-tabs-slider>

              <v-tab  href="#tab-1">
                General Question
                <v-icon>forum</v-icon>
              </v-tab>
              <v-tab href="#tab-2">
                Troubleshoot
                <v-icon>chat_bubble_outline</v-icon>
              </v-tab>
              <v-tab href="#tab-3">
                Development
                <v-icon>gavel</v-icon>
              </v-tab>
              <v-tab href="#tab-4">
                Licences
                <v-icon>history</v-icon>
              </v-tab>
              <v-tab href="#tab-4">
                Support
                <v-icon>help</v-icon>
              </v-tab>
              <v-tab href="#tab-5">
                My Account
                <v-icon>person_pin</v-icon>
              </v-tab>
                
                
          </v-tabs>


  <div class="container ">
    <v-layout row wrap>
      
      <v-flex xs12 sm12>
        <div class="pt-3 pb-3">
                <h3> General Question </h3> 
                <p> Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>


              </div>

        <v-toolbar card  color="white" class="pa-0">
               
                 <v-text-field class="pt-0"
                            prepend-icon="search"
                            placeholder=" Search tickets"                           
                           
                            hide-details
                          ></v-text-field>
               
               
                <v-btn icon>
                  <v-icon>apps</v-icon>
                </v-btn>
                <v-btn icon>
                  <v-icon>more_vert</v-icon>
                </v-btn>
              </v-toolbar>
              


          <v-expansion-panel focusable>
            <v-expansion-panel-content v-for="item in items ">
              <div slot="header" ><b>{{ item.title }} </b> </div>
              <v-card>
                <v-card-text class="grey lighten-3">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</v-card-text>
              </v-card>
            </v-expansion-panel-content>
          </v-expansion-panel>
      </v-flex>
      
    </v-layout>
       
  </div>
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
          selected_tab : 'tab-1',
          items : [
            { title : 'What is Sximo Console ?' , content : '' },
            { title : 'How its work ?' , content : '' },
            { title : 'Whats minimum requirment server .' , content : '' },
            { title : 'Will im able to customize the codes and whats easy ?' , content : '' },
            { title : 'Dormouse go on for some minutes. The Caterpillar and Alice looked very anxiously into' , content : '' },
            { title : 'Dormouse go on for some minutes. The Caterpillar and Alice looked very anxiously into' , content : '' },
            { title : 'Dormouse go on for some minutes. The Caterpillar and Alice looked very anxiously into' , content : '' },
            { title : 'Dormouse go on for some minutes. The Caterpillar and Alice looked very anxiously into' , content : '' },
          ],
           categories :[
            { title : 'Billing & Returs' , badge : '24' ,icon :'folder'},
            { title : 'Marketing', badge : '5' ,icon :'turned_in_not'},
            { title : 'Sales', badge : '1' ,icon :'turned_in_not'},
            { title : 'Supports', badge : '14' ,icon :'turned_in_not'}
          ],
        /* END Dinamic Data From CRUDENGINE */        
        //status_active: true   
          baseUrl : store.state.baseUrl +'helpdesk/hd_faq'
        
        }
    },    
    mounted: function () 
    {
        
          
    },
    methods : {
     


    }

}
</script>
