<template>
  <v-app light>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
      <v-list>
        <v-list-item
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
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>{{ title }}</v-toolbar-title>
      <v-spacer />

      <!-- ปุ่ม Logout -->
      <v-btn text @click="logout">
        Logout
      </v-btn>
    </v-app-bar>
    <v-main>
      <v-container>
        <Nuxt />
      </v-container>
    </v-main>
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    name: 'DefaultLayout',
    data () {
      return {
        clipped: false,
        drawer: false,
        fixed: false,
        items: [
          {
            icon: '',
            title: 'Home',
            to: '/'
          },
          {
            icon: '',
            title: 'หัวข้อหลักประเมินงานKpi',
            to: '/KeyPerformanceIndicator'
          },
          {
            icon: '',
            title: 'หัวข้อย่อยKpi',
            to: '/subtopic'
          },
          {
            icon: '',
            title: 'ประเมินKpi',
            to: '/report'
          },
          {
            icon: '',
            title: 'รายงาน',
            to: '/inspire'
          },
        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'ประเมินKpi'
      }
    }
  }
  </script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Kanit:wght@200;300;400;500;600;700&display=swap');

/* Apply the font to the appropriate elements */
body,
.v-toolbar__title,
.v-list-item__title {
  font-family: 'Kanit', sans-serif;
  color: white;
}

/* Change the background color of the toolbar */
.v-toolbar {
  background-color: #2a8445 !important;
}

/* Change the background color of the navigation drawer */
.v-navigation-drawer--fixed.theme--light {
  background-color: black;
}
.v-btn.v-btn--text.theme--light.v-size--default {
  color: #ffffff;
}
</style>
