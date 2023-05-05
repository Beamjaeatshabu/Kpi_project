<template>
  <v-app light>
    <v-navigation-drawer v-if="$route.path !== '/login'" v-model="drawer" :mini-variant="miniVariant" :clipped="clipped"
      fixed app class="v-navigation-drawer--open" style="background-color: #382c;">
      <v-list>
        <v-list-item v-for="(item, i) in items" :key="i" :to="item.to" router exact>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar :clipped-left="clipped" fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title><img src="logolpp2.jpg" height="40" width="60" alt="Logo"> </v-toolbar-title>
      <v-toolbar-title style="position: relative; left: 450px; font-family:'Kanit', sans-serif;">
        ประเมิน KPI
      </v-toolbar-title> <!-- ตำแหน่งสำหรับ title -->
      <v-toolbar-title v-if="$route.path !== '/login'"
        style="position: relative; left: 700px; font-family:'Kanit', sans-serif;">ชื่อผู้ใช้ : {{ email }}
      </v-toolbar-title> <!-- ตำแหน่งสำหรับ title -->
      <v-spacer />
      <!-- ปุ่ม Logout -->
      <!-- <v-btn v-if="!visible" to="/login">
        Login
      </v-btn> -->
      <v-btn v-if="visible" @click="logout">
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
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: true,
      visible: true,
      items: [
        {
          icon: '',
          title: 'กลุ่มหัวข้อหลักประเมิน KPI',
          to: '/KeyPerformanceIndicator'
        },
        {
          icon: '',
          title: 'หัวข้อหลักประเมิน KPI',
          to: '/subtopic'
        },
        {
          icon: '',
          title: 'หัวข้อย่อยประเมิน KPI',
          to: '/subtopic1'
        },
        {
          icon: '',
          title: 'การกำหนดหัวข้อประเมิน',
          to: '/evaluationtopics'
        },
        {
          icon: '',
          title: 'การประเมิน KPI ประจำปี',
          to: '/regularyear'
        },
        {
          icon: '',
          title: 'รายงานการประเมิน',
          to: '/report'
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'ประเมิน KPI '
    }
  },
  mounted() {
    this.visible_btn()
  },
  methods: {
    async visible_btn() {
      this.visible = this.$auth.loggedIn;
    },
    async logout() {
      await this.$auth.logout();
      this.$router.push('/login');
    }
  },
  watch: {
    $route() {
      location.reload();
    },
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Kanit:wght@200;300;400;500;600;700&display=swap');

/* Apply the font to the appropriate elements */
body,
.v-toolbar__title,
.v-list-item__title {
  color: white;
}

.v-navigation-drawer__content {
  background-color: #276445;
}

/* Change the background color of the toolbar */
.v-toolbar {
  background-color: #276445 !important;
}

/* Change the background color of the navigation drawer */
.v-navigation-drawer--fixed.theme--light {
  background-color: black;
}

.v-btn.v-btn--text.theme--light.v-size--default {
  color: #ffffff;
}

@media (max-width: 767px) {
  .logo-container {
    display: flex;
    justify-content: center;
  }

  .logo-container img {
    margin: 0;
  }

  .mobile-title {
    position: relative;
    left: 50px;
    text-align: center;
    font-family: 'Kanit', sans-serif;
  }
}
</style>
