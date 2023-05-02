<template>
  <v-card class="mx-auto my-12" width="400">
    <v-card-title>Login</v-card-title>
    <v-card-text>
      <v-sheet width="300" class="mx-auto">
        <v-form @submit.prevent="userLogin">
          <v-text-field v-model="email" label="Email"></v-text-field>
          <v-text-field v-model="password" type="password" label="Password"></v-text-field>
          <v-btn type="submit" block class="mt-2">Submit</v-btn>
        </v-form>
      </v-sheet>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    async userLogin(e) {
      try {
        e.preventDefault();
        const payload = {
          email: this.email,
          password: this.password
        };
        await this.$auth.loginWith('local', { data: payload })
        this.$router.push('/KeyPerformanceIndicator');
      } catch (e) {
        this.$router.push('/login');
      }
    }
  }
}
</script>
