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
              <v-list-item-title v-text="item.title" />
            </v-list-item-content>
          </v-list-item>
          <v-list-group v-else :prepend-icon="item.icon" no-action>
            <template v-slot:activator>
              <v-list-item-content>
                <v-list-item-title v-text="item.title"></v-list-item-title>
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

    <v-app-bar app hide-on-scroll height="60" elevate-on-scroll color="white">
      <v-app-bar-nav-icon class="hidden-md-and-up" @click="drawer = true" />
      <nuxt-link to="/" class="d-flex">
        <img :src="`log-exp.jpg`" alt="LogoExperta" />
      </nuxt-link>
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
                class="py-8 submenubtn hidden-sm-and-down"
                :ripple="false"
                v-bind="attrs"
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
          class="py-8 hidden-sm-and-down no-text-transform"
          :to="name.to"
          >{{ name.title }}</v-btn
        > </template
      ><v-spacer />
    </v-app-bar>
  </div>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      items: [
        {
          icon: 'mdi-folder-home-outline',
          title: 'Nosotros',
          to: '/',
        },
        {
          icon: 'mdi-account',
          title: 'Lineas de Negocio',
          to: '/about',
        },
        {
          icon: 'mdi-tools',
          title: 'Asegurate en Línea',
          to: '/services',
        },
        {
          icon: 'mdi-cash-usd',
          title: 'Operaciones',
          to: '/pricing',
        },
        {
          icon: 'mdi-folder-image',
          title: 'Alianzas Comerciales',
          to: '/gallery',
        },
        {
          icon: 'mdi-blogger',
          title: 'Campañas Digitales',
          to: '/blog',
        },
        {
          icon: 'mdi-contacts',
          title: 'Desarrollo Humano',
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
.submenubtn {
  cursor: default;
}

.v-btn {
  text-transform: none !important;
}
</style>
