<template>
       <v-app id="inspire">
    <div>
      <v-breadcrumbs :items="dulieu" divider=">" >
          <template v-slot:divider>
            <v-icon>mdi-forward</v-icon>
          </template>        
      </v-breadcrumbs>
      <v-breadcrumbs :dulieu="dulieu" divider="-"></v-breadcrumbs>
      <v-btn absolute
              @click="dialog = !dialog"
              fab
              fixed
              color ="pink">
            <v-icon>mdi-plus</v-icon>
                      <v-dialog v-model="dialog" max-width="500px">
            <v-card>
              <v-card-text>
                <v-text-field label="File name"></v-text-field>
  
                <small class="grey--text">* This doesn't actually save.</small>
              </v-card-text>
  
              <v-card-actions>
                <v-spacer></v-spacer>
  
                <v-btn text color="primary" @click="dialog = false">Submit</v-btn>
              </v-card-actions>
            </v-card>
          </v-dialog>
      </v-btn>
    </div>
         <div>
          <v-system-bar
              color="orange"
          >
            <v-icon>mdi-gmail</v-icon>
            <span>10 unread emails</span>
            <v-spacer></v-spacer>
            <v-icon>mdi-wifi-strength-4</v-icon>
            <v-icon>mdi-signal-cellular-outline</v-icon>
            <v-icon>mdi-battery</v-icon>
            <span>12:30</span>              
          </v-system-bar>
           <v-card>
          <v-app-bar color="red accent-4"
          dark
          shrink-on-scroll
          src="https://picsum.photos/1920/1080?random"
          scroll-target="#scrolling-techniques-2">
                <v-app-bar-nav-icon></v-app-bar-nav-icon>
                      <template v-slot:img="{ props }">
                        <v-img
                          v-bind="props"
                          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
                        ></v-img>
                      </template>
                          <v-toolbar-title>Home Page</v-toolbar-title>
                          <v-spacer></v-spacer>
                          <v-toolbar-items>
                            <v-btn text>News</v-btn>
                            <v-btn text>Tranfermart</v-btn>
                            <v-btn text>Discover</v-btn>
                          </v-toolbar-items>
                        <v-btn icon>
                          <v-icon>mdi-magnify</v-icon>
                        </v-btn>
                  
                        <v-btn icon>
                          <v-icon>mdi-heart</v-icon>
                        </v-btn>
                  
                        <v-btn icon>
                          <v-icon>mdi-dots-vertical</v-icon>
                        </v-btn>
              </v-app-bar>
              </v-card>
              <div>
                <v-bottom-sheet>
                  <template v-slot:activator="{ on }">
                      <v-btn
                        color="purple"
                        dark
                        v-on="on"
                      >
                        Open Usage
                      </v-btn>
                  </template>
                    <v-card class="text-cen" height="200px">
                        <v-container>
                          <v-row justify="space-between">
                            <v-col cols="auto">
                              <v-img
                                height="200"
                                width="200"
                                src="https://cdn.vuetifyjs.com/images/cards/store.jpg"
                              ></v-img>
                            </v-col>
                    
                            <v-col
                              cols="auto"
                              class="text-center pl-0"
                            >
                              <v-row
                                class="flex-column ma-0 fill-height"
                                justify="center"
                              >
                                <v-col class="px-0">
                                  <v-btn icon>
                                    <v-icon>mdi-heart</v-icon>
                                  </v-btn>
                                </v-col>
                    
                                <v-col class="px-0">
                                  <v-btn icon>
                                    <v-icon>mdi-bookmark</v-icon>
                                  </v-btn>
                                </v-col>
                    
                                <v-col class="px-0">
                                  <v-btn icon>
                                    <v-icon>mdi-share-variant</v-icon>
                                  </v-btn>
                                </v-col>
                              </v-row>
                            </v-col>
                          </v-row>
                        </v-container>
                    </v-card>                
                </v-bottom-sheet>
              </div>
              <v-carousel>
                  <v-carousel-item
                              v-for="(item,i) in items"
                              :key="i"
                              :src="item.src"
                              reverse-transition="fade-transition"
                              transition="fade-transition"
                  >
                  </v-carousel-item>
              </v-carousel>
         </div>
         <v-img
            :src="tieu"
            :lazy-src="tieu"
            aspect-ratio="1"
            class="grey lighten-2"
            max-width="500"
            max-height="300"
        >
         </v-img>
         <v-sheet>
            <v-calendar
              type="month"
              now="2019-11-27"
              value="2019-11-27"
              :events="events"
            >
            </v-calendar>
         </v-sheet>
            <v-bottom-navigation    
                grow
                horizontal
                shift
                color="deep-purple accent-4"
              >
                <v-btn value="recent">
                  <span>Recent</span>
                  <v-icon>mdi-history</v-icon>
                </v-btn>
            
                <v-btn value="favorites">
                  <span>Favorites</span>
                  <v-icon>mdi-heart</v-icon>
                </v-btn>
            
                <v-btn value="nearby">
                  <span>Nearby</span>
                  <v-icon>mdi-map-marker</v-icon>
                </v-btn>
              </v-bottom-navigation>         
       </v-app>
       
</template>

<script>

export default {
  name: 'App',

  components: {

  },

  data: () => ({
    tieu:require('../public/Book/7_CJQH.jpg'),
    items:[
      {src: require('../public/Book/2.jpg')},
      {src: require('../public/Book/3.jpg')},
      {src: require('../public/Book/4.jpg')},
      {src: require('../public/Book/e5.jpg')},
    ],
    dulieu:[
      {
        text: 'Dashboard',
        disabled: false,
        href: 'breadcrumbs_dashboard',
      },
      {
        text: 'Link 1',
        disabled: false,
        href: 'breadcrumbs_link_1',
      },
      {
        text: 'Link 2',
        disabled: true,
        href: 'breadcrumbs_link_2',
      },
    ],
    dialog:false,
    events: [
      {
        name: 'Vacation',
        start: '2018-12-30',
        end: '2019-01-02',
      },
      {
        name: 'Meeting',
        start: '2019-01-07',
      },
      {
        name: '30th Birthday',
        start: '2019-01-03',
      },
      {
        name: 'New Year',
        start: '2019-01-01',
      },
      {
        name: 'Conference',
        start: '2019-01-21',
      },
      {
        name: 'Hackathon',
        start: '2019-01-30',
        end: '2019-02-01',
      },
    ],

  }),
  
};
</script>
<style lang="stylus" scoped>

</style>
