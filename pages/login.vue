<template>
  <div class="container">
    <p>กรอกชื่อผู้ใช้งานและรหัสผ่าน เหมือน login เข้าเครื่อง</p>
    <form @submit.prevent="userLogin">
      <span for="email">ชื่อผู้ใช้งาน :</span>
      <input type="text" id="email" name="email" v-model="email">
      <br>
      <span for="password">รหัสผ่าน :</span>
      <input type="password" id="password" name="password" v-model="password">
      <br>
      <button type="submit" class="mt-2">Login</button>
      <div class="vertical-line"></div>
      <a class="f" href="https://selfservice.lpn.co.th:8888/ss" target="_blank">ลืมรหัสผ่าน/ปลดล็อค</a>
      <div class="long-line"></div>
    </form>
    <div>
      <img src="SERVICES30.jpg" alt="Alternative Text" class="my-image">
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
  box-shadow: inset 0 1px 3px rgba(0, 0, 0, .1);
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
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.3);
}

.long-line {
  position: relative;
  top: -60px;
  border-top: 2px solid #ddd;
  /* เส้นแนวนอนสีเทาเข้ม */
  height: 1px;
  /* ความสูงของเส้นแนวนอน */
  width: 100%;
  /* กว้างเท่ากับขนาดของ container */
}

.vertical-line {
  border-left: 2px solid #ddd;
  /* กำหนดเส้นตรงแนวตั้งด้านขวา */
  /* border-left: 2px solid black; */
  /* กำหนดเส้นตรงแนวตั้งด้านซ้าย */
  height: 45px;
  /* กำหนดความสูงของเส้น */
  position: relative;
  top: -63px;
  right: -100px;
}

.f {
  color: black;
  position: relative;
  top: -97px;
  right: -120px;
}
.my-image{
  width: 100%;
  position: relative;
  top: -40px;
}

@media (max-width: 767px) {

  input[type="text"],
  input[type="password"] {
    display: block;
    margin-bottom: 5px;
    border: 1px solid #ccc;
    border-radius: 3px;
    font-size: 16px;
    line-height: 1.5;
    box-shadow: inset 0 1px 3px rgba(0, 0, 0, .1);
    position: relative;
    left: 70px;
  }

  span {
    display: flex;
    flex-direction: column;
    position: relative;
    left: -10px;
    top:22px;
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
    box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.3);
  }

  .long-line {
    border-top: 2px solid #ddd;
    /* เส้นแนวนอนสีเทาเข้ม */
    height: 1px;
    /* ความสูงของเส้นแนวนอน */
    width: 100%;
    /* กว้างเท่ากับขนาดของ container */
  }

  .vertical-line {
    border-left: 2px solid #ddd;
    /* กำหนดเส้นตรงแนวตั้งด้านขวา */
    /* border-left: 2px solid black; */
    /* กำหนดเส้นตรงแนวตั้งด้านซ้าย */
    height: 45px;
    /* กำหนดความสูงของเส้น */
    position: relative;
    top: -63px;
    right: -100px;
  }

  .f {
    color: black;
    position: relative;
    top: -97px;
    right: -120px;

  }
  .container
  {
    width: 100%;
    padding: 12px;
    margin-right: auto;
    margin-left: auto;
    position: relative;
    left: 20px;
  }
}</style>
