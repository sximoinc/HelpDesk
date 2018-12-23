<template>
  <div>
     <v-tabs
              
              color="white"
              icons-and-text
              class="mb-0"
              centered
              v-model="selected_tab"
            >
             <v-tabs-slider color="indigo"></v-tabs-slider>

              <v-tab  href="#tab-1">
                Board
                <v-icon>forum</v-icon>
              </v-tab>
              <v-tab href="#tab-2">
                  Threads / Topic
                  <v-icon>chat_bubble_outline</v-icon>
                </v-tab>
                <v-tab href="#tab-3">
                  Posts
                  <v-icon>filter_none</v-icon>
                </v-tab>
                
          </v-tabs>

    <div class="container">

       <v-tabs-items  v-model="selected_tab">
          <v-tab-item id="tab-1" key="1">
                 
                    
              <v-toolbar card  color="transparent" class="pa-0">
               <v-btn  color="white" small  >
                  <v-icon>add</v-icon>  <span> new Forum </span> 
                </v-btn>

                <v-spacer></v-spacer>
                <v-btn icon>
                  <v-icon>apps</v-icon>
                </v-btn>
                <v-btn icon>
                  <v-icon>more_vert</v-icon>
                </v-btn>
              </v-toolbar>
              
               
              <v-layout row wrap class="mt-3">
                    <v-flex xs12 sm4 v-for="row in items_board">
                        <v-card class="ma-1 mb-2">
                            <v-card-title color="grey lighten-3">
                                 {{ row.board }}
                               </v-card-title>
                            <v-card-text  style="height: 280px; overflow: hidden;">
                                <div class="text-xs-center mb-3">
                                  <v-icon size="72" :color="row.color">{{ row.icon }}</v-icon>
                                </div>
                                <div v-html="row.description" class="mb-2"></div>
                                <div class="text-xs-center">
                                  <v-chip small outline @click="">                                   
                                    General Discussion
                                  </v-chip>
                                  <v-chip small outline @click="">                                   
                                    Customizataion
                                  </v-chip>
                                  <v-chip small outline @click="">                                   
                                    Request
                                  </v-chip>
                                  <v-chip small outline @click="">                                   
                                    Report Bug
                                  </v-chip>
                                </div>
                            </v-card-text>
                            <v-card-actions>
                              <v-btn color="success" flat small> <v-icon>chat_bubble_outline</v-icon> {{ row.topics }} </v-btn>
                              <v-spacer></v-spacer>
                              <v-btn color="success" flat small> <v-icon>filter_none</v-icon>  {{ row.posts }}  </v-btn>
                            </v-card-actions>
                        </v-card>
                    </v-flex>
                  </v-layout>         
            </v-tab-item>

                <v-tab-item id="tab-2" key="2">
                   <v-card flat>
                    <v-card-title >
                      Topic / Categories
                    </v-card-title>
                    <v-toolbar card prominent color="white">
                         <v-btn  color="indigo" dark small>
                            <span> Create new </span> 
                          </v-btn>

                          <v-spacer></v-spacer>
                            <v-autocomplete prepend-icon="filter_list" placeholder="Jump to forum   " ></v-autocomplete>
                          <v-spacer></v-spacer>                     
                           
                          <v-btn icon>
                            <v-icon>apps</v-icon>
                          </v-btn>
                          <v-btn icon>
                            <v-icon>more_vert</v-icon>
                          </v-btn>

                          
                        </v-toolbar>


                      <v-card-text >
                             <v-data-table
                               
                                :items="items_topic"
                                class="elevation-0"
                              >
                                <template slot="items" slot-scope="props">
                                    <td class="pt-3 pb-3">
                                      <h2 class="display-0 mb-1 mt-1"> 
                                        <a :to="'/helpdesk/thread?thread=1'">{{ props.item.title }}  </a></h2>
                                        <div v-html="props.item.description"></div>
                                       
                                    </td>
                                     <td> 
                                      <v-icon>filter_none</v-icon> {{ props.item.replies }}
                                    </td>
                                  </template>

                              </v-data-table> 
                      </v-card-text>
                    </v-card>
                </v-tab-item>

                <v-tab-item id="tab-3" key="3">
                    <v-card flat>
                    <v-card-title >
                      Topic
                    </v-card-title>
                      <v-card-text >
                             <v-toolbar card prominent color="white">
                         <v-btn  color="indigo" dark small>
                            <span> Create new </span> 
                          </v-btn>

                          <v-spacer></v-spacer>
                           <v-text-field class="pt-0"
                            prepend-icon="search"
                            placeholder=" Search Posts"                           
                           
                            hide-details
                          ></v-text-field>
                          <v-autocomplete prepend-icon="filter_list" placeholder="Thread / Topic  " ></v-autocomplete>
                          <v-spacer></v-spacer>                     
                           
                          <v-btn icon>
                            <v-icon>apps</v-icon>
                          </v-btn>
                          <v-btn icon>
                            <v-icon>more_vert</v-icon>
                          </v-btn>

                          
                        </v-toolbar>


                      
                             <v-data-table
                               
                                :items="items_topic"
                                class="elevation-0"
                              >
                                <template slot="items" slot-scope="props">
                                    <td class="pt-2 pb-2">
                                      <h3 class="display-0 mb-1 mt-1"> 
                                        <a :to="'/helpdesk/thread?thread=1'">{{ props.item.title }} ( {{ props.item.replies }} )</a></h3>
                                        
                                        <p class="mt-3">Posted By : Gyan Silva 3 days ago on Request Features</p>
                                    </td>
                                    <td></td>
                                    <td> 
                                      <v-icon>comment</v-icon> 25
                                    </td>
                                                                       
                                    
                                  </template>

                              </v-data-table> 

                      </v-card-text>
                    </v-card>
                </v-tab-item>
         </v-tabs-items>    
       
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
          selected_tab :'tab-1' ,
           headers_board: [
            { text: 'Board / Category', value: 'board' },
            { text: 'Description', value: 'description' },
            { text: 'Topics', value: 'topics' },
            { text: 'Posts', value: 'posts' },

          ],
          items_board : [],
          headers_topic: [
            { text: 'Topic', value: 'topic' },
            { text: 'Replies', value: 'Replies' },
            { text: 'Started', value: 'started' },
            { text: 'Created', value: 'created' },

          ],
          headers_thread: [
            { text: 'Topic', value: 'topic' },
            { text: 'Replies', value: 'Replies' },
            { text: 'Started', value: 'started' },
            { text: 'Created', value: 'created' },

          ],
        /* END Dinamic Data From CRUDENGINE */        
        //status_active: true   
          baseUrl : store.state.baseUrl +'helpdesk/discussion'
        
        }
    },    
    mounted: function () 
    {
       
        this.items_board = [
          { board : 'Sximo 5 Discussion' , description : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin id euismod tellus, eget ullamcorper neque. Vestibulum pharetra tristique aliquet. Cras sollicitudin sapien et ipsum finibus, et sagittis magna vulputate.' , topics : '16' , posts : '112' , icon :'perm_contact_calendar' , color : 'purple' },
          { board : 'Sximo Ultimate' , description : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin id euismod tellus, eget ullamcorper neque. Vestibulum pharetra tristique aliquet. Cras sollicitudin sapien et ipsum finibus, et sagittis magna vulputate.' , topics : '13' , posts : '112' ,icon :'markunread_mailbox' , color : 'teal' },
          { board : 'Sximo Console' , description : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin id euismod tellus, eget ullamcorper neque. Vestibulum pharetra tristique aliquet. Cras sollicitudin sapien et ipsum finibus, et sagittis magna vulputate.' , topics : '4' , posts : '112' , icon:'language' , color : 'indigo' },
          { board : 'Sximo UI' , description : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin id euismod tellus, eget ullamcorper neque. Vestibulum pharetra tristique aliquet. Cras sollicitudin sapien et ipsum finibus, et sagittis magna vulputate.' , topics : '3' , posts : '112' , icon:'favorite' , color : 'pink'},
          { board : 'Sximo DataTable' , description : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin id euismod tellus, eget ullamcorper neque. Vestibulum pharetra tristique aliquet. Cras sollicitudin sapien et ipsum finibus, et sagittis magna vulputate.' , topics : '3' , posts : '112' , icon:'duo' , color : 'green'},
          { board : 'Sximo Press' , description : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin id euismod tellus, eget ullamcorper neque. Vestibulum pharetra tristique aliquet. Cras sollicitudin sapien et ipsum finibus, et sagittis magna vulputate.' , topics : '3' , posts : '112' , icon:'chat_bubble' , color : 'orange'}
        ]   

        this.items_topic = [
          { title : 'General Discussion' , description : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin id euismod tellus, eget ullamcorper neque. Vestibulum pharetra tristique aliquet. Cras sollicitudin sapien et ipsum finibus, et sagittis magna vulputate.' , replies : '16' , posts : '112'},
          { title : 'Report Bugs' , description : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin id euismod tellus, eget ullamcorper neque. Vestibulum pharetra tristique aliquet. Cras sollicitudin sapien et ipsum finibus, et sagittis magna vulputate.' , replies : '13' , posts : '112'},
          { title : 'Customization' , description : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin id euismod tellus, eget ullamcorper neque. Vestibulum pharetra tristique aliquet. Cras sollicitudin sapien et ipsum finibus, et sagittis magna vulputate.' , replies : '4' , posts : '112'},
          { title : 'Request Features' , description : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin id euismod tellus, eget ullamcorper neque. Vestibulum pharetra tristique aliquet. Cras sollicitudin sapien et ipsum finibus, et sagittis magna vulputate.' , replies : '3' , posts : '112'}
        ] 

    },
    methods : {
     


    }

}
</script>
<style type="text/css">
  .v-chip .v-chip__content {
    font-size: 11px;
  }
</style>
