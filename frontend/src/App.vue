<template>
  <v-app id="inspire">

    <v-app-bar app clipped-right color="blue-grey" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Toolbar</v-toolbar-title>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" app>
      <v-list dense>

        <v-list-item v-for="(route, index) in routes" :key="index" @click.stop="left = !left" :to="{path: route.path}">
          <v-list-item-action>
            <v-icon>{{ route.icon }}</v-icon>
          </v-list-item-action>

          <v-list-item-content>
            <v-list-item-title>
              {{ route.name }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>

      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container fluid>
        <v-row>
          <router-view/>
        </v-row>
      </v-container>
    </v-main>

  </v-app>
</template>

<script>
export default {
    props: {
      source: String,
    },
    data: () => ({
      drawer: null,
      drawerRight: null,
      right: false,
      left: false,
      routes: [
        {
          'path': '/',
          'name': 'Home',
          'icon': 'mdi-exit-to-app'
        },
        {
          'path': '/pages',
          'name': 'Pages',
          'icon': 'mdi-event'
        }
      ]
    }),
  }
</script>