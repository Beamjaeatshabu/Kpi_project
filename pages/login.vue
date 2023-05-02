<template>
  <div>
    <p>กรอกชื่อผู้ใช้งานและรหัสผ่าน เหมือน login เข้าเครื่อง</p>
    <div>
      <form @submit.prevent="userLogin">
        <span for="email">ชื่อผู้ใช้งาน :</span>
        <input type="text" id="email" name="email" v-model="email">
        <br>
        <span for="password">รหัสผ่าน :</span>
        <input type="password" id="password" name="password" v-model="password">
        <br>
        <button type="submit" class="mt-2">Login</button> 
        <div class="vertical-line"></div>
        <div class="long-line"></div>
      </form>
    </div>
  </div>
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

<style scoped>
div {
  font-family: 'Kanit', sans-serif;
}

input[type="text"],
input[type="password"] {
  display: block;
  margin-bottom: 5px;
  border: 1px solid #ccc;
  border-radius: 3px;
  font-size: 16px;
  line-height: 1.5;
}

span {
  display: flex;
  flex-direction: column;
}

button {
  background-color: darkgreen;
  border: none;
  color: #fff;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  border-radius: 4px;
  margin-right: 10px;
  margin-bottom: 20px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
  font-family: 'Kanit', sans-serif;
  display: right;
}
.long-line {
  border-top: 2px solid #ddd; /* เส้นแนวนอนสีเทาเข้ม */
  height: 1px; /* ความสูงของเส้นแนวนอน */
  width: 100%; /* กว้างเท่ากับขนาดของ container */
}

</style>
