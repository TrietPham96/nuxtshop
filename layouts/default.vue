<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
      color="#171f36"
      dark
      height="100%"
    >
      <v-list>
        <v-list-item to="/" router exact>
          <v-list-item-action>
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="'Home'" />
          </v-list-item-content>
        </v-list-item>
        <!-- <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item> -->
        <v-list-group prepend-icon="mdi-shopping" no-action>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title>Shop</v-list-item-title>
            </v-list-item-content>
          </template>
          
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
            :href="item.to"
            router
            exact
          >
            <v-list-item-content>
              <v-list-item-title v-text="item.title"></v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
        <v-list-item to="/product" router exact>
          <v-list-item-action>
            <v-icon>mdi-tshirt-v</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="'Product'" />
          </v-list-item-content>
        </v-list-item>
        <v-list-item to="/blog" router exact>
          <v-list-item-action>
            <v-icon>mdi-post-outline</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="'Blog'" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" app color="primary" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title style="width: 350px">
        <a href="/" class="white--text" style="text-decoration: none"
          ><v-icon>mdi-truck</v-icon>&nbsp;ShipIT</a
        >
      </v-toolbar-title>
      <v-text-field
        flat
        solo-inverted
        hide-details
        prepend-inner-icon="mdi-magnify"
        label="Search"
        class="hidden-sm-and-down pl-10 ml-4"
      />
      <v-spacer />
      <v-btn icon>
        <v-icon>mdi-account-circle</v-icon>
      </v-btn>
      <v-btn icon>
        <v-badge content="2" value="2" color="green" overlap>
          <v-icon>mdi-bell</v-icon>
        </v-badge>
      </v-btn>
      <v-btn to="/cart" icon>
        <v-badge content="2" value="2" color="green" overlap>
          <v-icon>mdi-cart</v-icon>
        </v-badge>
      </v-btn>
    </v-app-bar>
    <v-main>
      <Nuxt />
    </v-main>
    <v-footer :padless="true" :style="{ 'z-index': zIndex }">
      <v-card width="100%" class="accent">
        <v-container>
          <v-row no-gutters>
            <v-col class="col-12 col-md-4 col-sm-12">
              <v-row>
                <v-col class="col-12 col-sm-3 pr-4" align="right">
                  <v-icon class="display-2">mdi-truck</v-icon>
                </v-col>
                <v-col class="col-12 col-sm-9 pr-4">
                  <h3 class="font-weight-light">FREE SHIPPING & RETURN</h3>
                  <p class="font-weight-thin">Free Shipping over $300</p>
                </v-col>
              </v-row>
            </v-col>
            <v-col class="col-12 col-md-4 col-sm-12">
              <v-row>
                <v-col class="col-12 col-sm-3 pr-4" align="right">
                  <v-icon class="display-2">mdi-cash</v-icon>
                </v-col>
                <v-col class="col-12 col-sm-9 pr-4">
                  <h3 class="font-weight-light">MONEY BACK GUARANTEE</h3>
                  <p class="font-weight-thin">30 Days Money Back Guarantee</p>
                </v-col>
              </v-row>
            </v-col>
            <v-col class="col-12 col-md-4 col-sm-12">
              <v-row>
                <v-col class="col-12 col-sm-3 pr-4" align="right">
                  <v-icon class="display-2">mdi-headset</v-icon>
                </v-col>
                <v-col class="col-12 col-sm-9 pr-4">
                  <h3 class="font-weight-light">020-800-456-747</h3>
                  <p class="font-weight-thin">24/7 Available Support</p>
                </v-col>
              </v-row>
            </v-col>
          </v-row>
        </v-container>
      </v-card>
      <v-card flat tile width="100%" class="secondary white--text text-center">
        <v-card-text>
          <v-btn class="mx-4 white--text" icon>
            <v-icon size="24px">mdi-home</v-icon>
          </v-btn>
          <v-btn class="mx-4 white--text" icon>
            <v-icon size="24px">mdi-email</v-icon>
          </v-btn>
          <v-btn class="mx-4 white--text" icon>
            <v-icon size="24px">mdi-calendar</v-icon>
          </v-btn>
          <v-btn class="mx-4 white--text" icon>
            <v-icon size="24px">mdi-delete</v-icon>
          </v-btn>
        </v-card-text>

        <v-card-text class="white--text pt-0">
          Phasellus feugiat arcu sapien, et iaculis ipsum elementum sit amet.
          Mauris cursus commodo interdum. Praesent ut risus eget metus luctus
          accumsan id ultrices nunc. Sed at orci sed massa consectetur dignissim
          a sit amet dui. Duis commodo vitae velit et faucibus. Morbi vehicula
          lacinia malesuada. Nulla placerat augue vel ipsum ultrices, cursus
          iaculis dui sollicitudin. Vestibulum eu ipsum vel diam elementum
          tempor vel ut orci. Orci varius natoque penatibus et magnis dis
          parturient montes, nascetur ridiculus mus.
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text class="white--text">
          {{ new Date().getFullYear() }} — <strong>ShipIT</strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "DefaultLayout",
  data() {
    return {
      clipped: true,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: "",
          title: "T-Shirts",
          to: "/shop",
        },
        {
          icon: "",
          title: "Jackets",
          to: "/shop",
        },
        {
          icon: "",
          title: "Shirts",
          to: "/shop",
        },
        {
          icon: "",
          title: "Jeans",
          to: "/shop",
        },
        {
          icon: "",
          title: "Shoes",
          to: "/shop",
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: "Vuetify.js",
    };
  },
  computed: {
    zIndex() {
      switch (this.$vuetify.breakpoint.name) {
        case "xs":
          return 1;
        case "sm":
          return 1;
        case "md":
          return 10;
        case "lg":
          return 10;
        case "xl":
          return 10;
      }
    },
  },
};
</script>
