<template>
  <v-app>
    <!-- Appbar -->
    <v-app-bar app color="white">
      <v-app-bar-nav-icon class="hidden-md-and-up" v-on:click="toggleDrawer" />

      <div class="d-flex align-center">
        <v-img class="shrink mr-2" contain width="30" src="@/assets/logo.png" />
      </div>
      <v-toolbar-title class="headline">
        SafeHouse
      </v-toolbar-title>
      <v-spacer class="hidden-xs-only" />

      <v-btn
        v-for="([link, text], i) in links"
        :key="i"
        :to="link"
        class="font-weight-light hidden-sm-and-down ml-2"
        color="red"
        large
        text
      >
        {{ text }}
      </v-btn>
    </v-app-bar>
    <!-- End of Appbar -->
    <!-- Drawer  -->
    <v-navigation-drawer v-model="drawer" fixed light temporary>
      <v-list>
        <v-list-item v-for="([link, text], i) in links" :key="i" :to="link">
          <v-list-item-title v-text="text" />
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <!-- End of Drawer  -->

    <v-content>
      <base-jumbotron
        :src="require('@/assets/bed.jpg')"
        light
        width="100%"
        min-height="100vh"
      >
        <v-row align="center" class="pb-12">
          <v-col cols="12" md="5">
            <div>
              <base-title class="white--text">
                Safe House Inc
              </base-title>
              <div class="body-1 white--text">
                connecting people in times of need.
              </div>
            </div>
          </v-col>
        </v-row>
      </base-jumbotron>
      <!-- Search Filter  -->
      <base-card>
        <v-form>
          <v-container>
            <v-row>
              <v-col cols="6">
                <v-select
                  v-bind:items="categories"
                  label="I'm searching for..."
                >
                </v-select>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="6">
                <v-select v-bind:items="locations" label="Location"> </v-select>
              </v-col>
              <v-col cols="6">
                <v-select v-bind:items="distances" label="Distance"> </v-select>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <v-btn type="submit" primary color="blue" class="white--text"
                  >Search</v-btn
                >
              </v-col>
            </v-row>
          </v-container>
        </v-form>
        <!-- End Search Filter  -->
        <!-- Article -->
        <v-container>
          <v-row>
            <v-col>
              <v-card>
                <v-card-title>
                  Malaysia Lockdown: Latest space for sharing in Singapore
                </v-card-title>
                <v-card-text>
                  Due to Malaysia lockdown, we are connecting workers who are
                  unable to find shelters to property owners who are willing to
                  share their space during this period.
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
        <!-- End Of Article -->
        <!-- Rooms -->
        <v-container>
          <v-row>
            <v-col cols="6" v-for="(room, index) in rooms" v-bind:key="index">
              <v-card>
                <v-card-title>
                  <v-img :src="room.src" contain />
                </v-card-title>
                <v-card-subtitle>
                  <v-subheader>
                    {{ room.type }}
                  </v-subheader>
                  {{ room.location }}
                </v-card-subtitle>
                <v-card-text>
                  {{ room.description }}
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
        <!-- End of Rooms -->
      </base-card>
    </v-content>
  </v-app>
</template>

<script>
// import Safehouse from "@/views/Safehouse";

export default {
  name: "App",

  components: {},
  data() {
    return {
      drawer: false,
      links: [["/", "Home"]],
      categories: ["1 Bed", "2 Bed"],
      locations: ["Singapore"],
      distances: ["< 50Km"],
      rooms: [
        {
          src:
            "https://www.asiaone.com/sites/default/files/styles/article_main_image/public/original_images/May2019/260419_design_homedecor_0.jpg?itok=ZLzevv_r",
          type: "HDB",
          location: "SERANGOON",
          description: "Two bedrooms available for rent with wifi, air-con and",
          bed: 2,
          bathroom: 2,
          like: 200
        },
        {
          src:
            "https://www.asiaone.com/sites/default/files/styles/article_main_image/public/original_images/May2019/260419_design_homedecor_0.jpg?itok=ZLzevv_r",
          type: "HDB",
          location: "SERANGOON",
          description: "Two bedrooms available for rent with wifi, air-con and",
          bed: 2,
          bathroom: 2,
          like: 200
        },
        {
          src:
            "https://www.asiaone.com/sites/default/files/styles/article_main_image/public/original_images/May2019/260419_design_homedecor_0.jpg?itok=ZLzevv_r",
          type: "HDB",
          location: "SERANGOON",
          description: "Two bedrooms available for rent with wifi, air-con and",
          bed: 2,
          bathroom: 2,
          like: 200
        },
        {
          src:
            "https://www.asiaone.com/sites/default/files/styles/article_main_image/public/original_images/May2019/260419_design_homedecor_0.jpg?itok=ZLzevv_r",
          type: "HDB",
          location: "SERANGOON",
          description: "Two bedrooms available for rent with wifi, air-con and",
          bed: 2,
          bathroom: 2,
          like: 200
        }
      ],
      items: [
        {
          src:
            "https://images-na.ssl-images-amazon.com/images/I/81VdNJravmL._SL1500_.jpg",
          item: "Toothbrush",
          price: "$1.00",
          description: "New toothbrush"
        },
        {
          src:
            "https://images-na.ssl-images-amazon.com/images/I/81VdNJravmL._SL1500_.jpg",
          name: "Toothbrush",
          price: "$1.00",
          description: "AnotherNew toothbrush"
        }
      ]
    };
  },
  methods: {
    getImgUrl: function(img) {
      var images = require.context("./assets/", false, /\.jpg$/);
      console.log(images("./" + img + ".jpg"));
      return images("./" + img + ".jpg");
    },
    toggleDrawer: function() {
      this.drawer = !this.drawer;
    }
  }
};
</script>
