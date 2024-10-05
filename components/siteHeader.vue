<template>
  <div>
    <v-navigation-drawer v-model="drawer" fixed app temporary>
      <v-list dense>
        <v-list-item-group v-for="(item, i) in items" :key="i" color="primary">
          <v-list-item v-if="!item.submenu" :to="item.to">
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title v-text="item.title.toUpperCase()" />
            </v-list-item-content>
          </v-list-item>
          <v-list-group v-else :prepend-icon="item.icon" no-action>
            <template v-slot:activator>
              <v-list-item-content>
                <v-list-item-title
                  v-text="item.title.toUpperCase()"
                ></v-list-item-title>
              </v-list-item-content>
            </template>
            <v-list-item
              v-for="child in item.submenu"
              :key="child.title"
              :to="child.to"
            >
              <v-list-item-content>
                <v-list-item-title v-text="child.title"></v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>

    <!--MOBILE VIEW-->
    <v-app-bar fixed app hide-on-scroll height="74" elevate-on-scroll>
      <v-app-bar-nav-icon class="hidden-md-and-up" @click="drawer = true" />
      <v-img class="logo-style-menu" :src="image"> </v-img>
      <v-spacer />
      <template v-for="(name, menuitem) in items">
        <template v-if="name.submenu">
          <v-menu
            :key="menuitem"
            open-on-hover
            offset-y
            transition="slide-y-transition"
            bottom
          >
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                plain
                class="py-5 submenubtn hidden-sm-and-down"
                :ripple="false"
                v-bind="attrs"
                style="height: auto"
                v-on="on"
              >
                {{ name.title }}
                <v-icon right small class="mx-0"> mdi-chevron-down </v-icon>
              </v-btn>
            </template>
            <v-list dense>
              <v-list-item
                v-for="(item, index) in name.submenu"
                :key="index"
                link
                :to="item.to"
              >
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </template>
        <v-btn
          v-else
          :key="menuitem"
          depressed
          tile
          plain
          class="py-8 hidden-sm-and-down"
          :to="name.to"
          >{{ name.title }}</v-btn
        > </template
      ><v-spacer />

      <v-btn icon @click="changeThemeColor">
        <v-icon>{{
          $vuetify.theme.dark ? 'mdi-white-balance-sunny' : 'mdi-weather-night'
        }}</v-icon>
      </v-btn>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  data() {
    return {
      image: require('@/static/annalogo.png'),
      clipped: false,

      drawer: false,
      items: [
        {
          icon: 'mdi-folder-home-outline',
          title: 'Home',
          to: '/',
        },
        {
          icon: 'mdi-account',
          title: 'Rreth nesh',
          to: '/about',
        },
        {
          icon: 'mdi-folder-image',
          title: 'Photography Gallery',
          to: '/gallery',
        },
        // {
        //   icon: 'mdi-tools',
        //   title: 'Sherbimet tona',
        //   to: '/services',
        //   submenu: [
        //     {
        //       title: 'Services Page',
        //       to: '/services',
        //     },
        //     {
        //       title: 'Static Websites',
        //       to: '/#',
        //     },
        //     {
        //       title: 'Mobile Applications',
        //       to: '/#',
        //     },
        //     {
        //       title: 'Corporate websites',
        //       to: '/#',
        //     },
        //     {
        //       title: 'Editorial Sites',
        //       to: '/#',
        //     },
        //     {
        //       title: 'Ecommerce and Store',
        //       to: '/#',
        //     },
        //     {
        //       title: 'Block Chain Devemopment',
        //       to: '/#',
        //     },
        //   ],
        // },
        {
          icon: 'mdi-cash-usd',
          title: 'Anna dekor',
          to: '/pricing',
        },
        {
          icon: 'mdi-folder-image',
          title: 'Decor Gallery',
          to: '/gallery',
        },
        // {
        //   icon: 'mdi-blogger',
        //   title: 'Blog',
        //   to: '/blog',
        // },
        {
          icon: 'mdi-contacts',
          title: 'Contact',
          to: '/contact',
        },
      ],
    }
  },
  methods: {
    changeThemeColor() {
      if (this.$vuetify.theme.dark === true) {
        this.$vuetify.theme.dark = false
      } else {
        this.$vuetify.theme.dark = true
      }
    },
  },
}
</script>

<style scoped>
.logo-style-menu {
  height: auto !important;
  width: auto;
  max-height: 70px;
  max-width: 100px;
  object-fit: contain !important;
  margin-left: 100px;
}

.submenubtn {
  cursor: default;
}
</style>
