<template>
  <div class=" ">
     <v-tabs
              
              color="white"
              icons-and-text
              class="mb-2"
              centered
              
              v-model="selected_tab"
            >
             <v-tabs-slider color="indigo"></v-tabs-slider>

              <v-tab  href="#tab-1">
                Sximo5 LTS
                <v-icon>forum</v-icon>
              </v-tab>
              <v-tab href="#tab-2">
                Sximo Ultimate
                <v-icon>chat_bubble_outline</v-icon>
              </v-tab>
              <v-tab href="#tab-3">
                Sximo Console
                <v-icon>gavel</v-icon>
              </v-tab>
              <v-tab href="#tab-4">
                Sximo Press
                <v-icon>history</v-icon>
              </v-tab>
              <v-tab href="#tab-4">
                Sximo DataTables
                <v-icon>help</v-icon>
              </v-tab>
              <v-tab href="#tab-5">
                My Account
                <v-icon>person_pin</v-icon>
              </v-tab>
                
                
          </v-tabs>
  <div class="container">
    <v-card>
      <v-card-title >
        Documentation
      </v-card-title>
      <v-card-text>
          <v-layout row wrap>
            <v-flex xs12 sm3>
              <v-treeview :items="items"

              >
                  <template slot="prepend" slot-scope="{ item, open, leaf }">
                    <v-icon   flat>bookmark_border</v-icon>
                   
                  </template>


              </v-treeview>

            </v-flex>
            <v-flex xs12 sm9>
              <h2>Quick start</h2>
                <p>Use one of the Vuetify Vue CLI packages (based on the official examples) to get your project started in no time. Vuetify supports SSR (server-side rendering), SPA (single page application), PWA (progressive web application) and standard HTML pages.

</p>
              <h2>Supported Browsers</h2>
              <p>Vuetify is a progressive framework that attempts to push web development to the next level. In order to best accomplish this task, some sacrifices had to be made in terms of support for older versions of Internet Explorer. This is not an exhaustive list of compatible browsers, but the main targeted ones.</p>
              <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin id euismod tellus, eget ullamcorper neque. Vestibulum pharetra tristique aliquet. Cras sollicitudin sapien et ipsum finibus, et sagittis magna vulputate. Suspendisse at pellentesque ante, ut fermentum nunc. Maecenas posuere nec odio at aliquam. Suspendisse non dictum leo, id venenatis massa. Morbi rhoncus est sed nibh ullamcorper bibendum. Fusce vitae turpis urna. Aliquam tellus lorem, faucibus id orci quis, commodo faucibus felis. Donec nec sem in ante luctus imperdiet in laoreet nisi. Ut faucibus eros enim, a auctor ante hendrerit vitae. Etiam id nunc est. Aliquam commodo nibh sit amet finibus placerat.</p>

              <p> Vestibulum in hendrerit enim. Praesent mollis mattis nulla sit amet aliquam. Nulla imperdiet efficitur sollicitudin. Suspendisse quis magna vitae urna ultricies commodo. Cras vel ex eu justo commodo bibendum non vitae odio. Proin vel neque laoreet, malesuada leo sed, ultricies sem. Quisque arcu dui, ullamcorper ac pretium vel, gravida ac magna. Vestibulum varius a augue ac euismod. Cras quis dui a tellus posuere bibendum. Vivamus elit turpis, hendrerit pellentesque lectus vitae, luctus posuere sapien. Mauris sed suscipit sapien. Quisque fringilla vel libero vitae euismod. Etiam aliquam eu odio vel blandit. Morbi euismod dapibus tellus at ornare. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Interdum et malesuada fames ac ante ipsum primis in faucibus.</p>
              <hr />
              <h3>New applications </h3>
              <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin id euismod tellus, eget ullamcorper neque. Vestibulum pharetra tristique aliquet. Cras sollicitudin sapien et ipsum finibus, et sagittis magna vulputate. Suspendisse at pellentesque ante, ut fermentum nunc. Maecenas posuere nec odio at aliquam. Suspendisse non dictum leo, id venenatis massa. Morbi rhoncus est sed nibh ullamcorper bibendum. Fusce vitae turpis urna. Aliquam tellus lorem, faucibus id orci quis, commodo faucibus felis. Donec nec sem in ante luctus imperdiet in laoreet nisi. Ut faucibus eros enim, a auctor ante hendrerit vitae. Etiam id nunc est. Aliquam commodo nibh sit amet finibus placerat.</p>

              <p> Vestibulum in hendrerit enim. Praesent mollis mattis nulla sit amet aliquam. Nulla imperdiet efficitur sollicitudin. Suspendisse quis magna vitae urna ultricies commodo. Cras vel ex eu justo commodo bibendum non vitae odio. Proin vel neque laoreet, malesuada leo sed, ultricies sem. Quisque arcu dui, ullamcorper ac pretium vel, gravida ac magna. Vestibulum varius a augue ac euismod. Cras quis dui a tellus posuere bibendum. Vivamus elit turpis, hendrerit pellentesque lectus vitae, luctus posuere sapien. Mauris sed suscipit sapien. Quisque fringilla vel libero vitae euismod. Etiam aliquam eu odio vel blandit. Morbi euismod dapibus tellus at ornare. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Interdum et malesuada fames ac ante ipsum primis in faucibus.</p>
              
            </v-flex>
          </v-layout>
      </v-card-text>

    </v-card>
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
          items: [
        {
          id: 1,
          name: 'Overview :',
          children: [
            { id: 2, name: 'Calendar : app' },
            { id: 3, name: 'Chrome : app' },
            { id: 4, name: 'Webstorm : app' }
          ]
        },
        {
          id: 5,
          name: 'Getting Started :',
          children: [
            {
              id: 6,
              name: 'vuetify :',
              children: [
                {
                  id: 7,
                  name: 'src :',
                  children: [
                    { id: 8, name: 'index : ts' },
                    { id: 9, name: 'bootstrap : ts' }
                  ]
                }
              ]
            },
            {
              id: 10,
              name: 'material2 :',
              children: [
                {
                  id: 11,
                  name: 'src :',
                  children: [
                    { id: 12, name: 'v-btn : ts' },
                    { id: 13, name: 'v-card : ts' },
                    { id: 14, name: 'v-window : ts' }
                  ]
                }
              ]
            }
          ]
        },
        {
          id: 15,
          name: 'Developments :',
          children: [
            { id: 16, name: 'October : pdf' },
            { id: 17, name: 'November : pdf' },
            { id: 18, name: 'Tutorial : html' }
          ]
        },
        {
          id: 19,
          name: 'Customization :',
          children: [
            {
              id: 20,
              name: 'Tutorials :',
              children: [
                { id: 21, name: 'Basic layouts : mp4' },
                { id: 22, name: 'Advanced techniques : mp4' },
                { id: 23, name: 'All about app : dir' }
              ]
            },
            { id: 24, name: 'Intro : mov' },
            { id: 25, name: 'Conference introduction : avi' }
          ]
        }
      ],
        /* END Dinamic Data From CRUDENGINE */        
        //status_active: true   
          baseUrl : store.state.baseUrl +'helpdesk/documentation'
        
        }
    },    
    mounted: function () 
    {
       
          
    },
    methods : {
     


    }

}
</script>
<style type="text/css">
  .v-treeview-node__label {
    font-size: 13px !important;
  }
</style>
