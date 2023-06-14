<template>
  <div class="container">
    <v-layout full-height>
      <v-app-bar
          color="primary"
          prominent
      >
        <v-app-bar-nav-icon variant="tonal" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title>My files</v-toolbar-title>
        <v-spacer></v-spacer>
      </v-app-bar>
      <v-navigation-drawer
          v-model="drawer"
          location="left"
      >
        <v-list :nav="true">
            <span v-for="item in items">
              <v-list-item :key="item.title" :to="item.route" :append-icon="item.icon"
                           :title="item.title" v-if="!item.is_expandable"></v-list-item>
              <v-list-group v-if="item.is_expandable" :key="item.value">
                <template v-slot:activator="{props}">
                  <v-list-item v-bind="props" title="Commons"></v-list-item>
                </template>
                <v-list-item v-for="child in item.children" :to="child.route" :value="child.value"
                             :title="child.title"
                             :append-icon="child.icon">
                </v-list-item>
              </v-list-group>
            </span>
        </v-list>
      </v-navigation-drawer>
      <v-main>
        <v-container :fluid="true">
          <slot/>
        </v-container>
        <v-footer fixed="true" color="primary" prominent class="d-flex flex-column" padless>
          <v-col class="text-center mt-4" cols="12">
            {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
          </v-col>
        </v-footer>
      </v-main>
    </v-layout>
  </div>
</template>

<script>
export default {
  name: 'Sidenav',
  data: () => ({
    drawer: true,
    group: null,
    open: 'commons',
    items: [
      {
        title: 'Dashboard',
        value: 'dashboard',
        icon: 'mdi-view-dashboard',
        route: '/dashboard',
        is_expandable: false,
        children: []
      },
      {
        title: 'Settings',
        value: 'settings',
        icon: 'mdi-cog',
        route: '/settings',
        is_expandable: false,
        children: []
      },
      {
        title: 'Commons',
        value: 'commons',
        icon: 'mdi-tune',
        is_expandable: true,
        children: [
          {
            title: 'Departments',
            value: 'departments',
            icon: 'mdi-office-building',
            route: '/commons/departments',
          }, {
            title: 'Users',
            value: 'user',
            icon: 'mdi-account-multiple',
            route: '/commons/users',
          },
        ]
      }
    ]
  }),

  watch: {
    group() {
      this.drawer = false
    },
  },
}
</script>