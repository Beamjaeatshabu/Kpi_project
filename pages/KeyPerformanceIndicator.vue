<template>
  <div class="container">
  <div>
    <form>
      <div>
        <label for="short-title">หัวข้อย่อ:</label>
        <input id="short-title" v-model="shortTitle" type="text" />
      </div>
      <div>
        <label for="sub-title">ชื่อหัวข้อย่อย:</label>
        <input id="sub-title" v-model="subTitle" type="text" />
      </div>
      <div>
        <label for="description">คำอธิบาย:</label>
        <input id="description" v-model="description" type="text" />
        <v-btn icon @click="submit">
          <v-icon class="my-icon white--text">mdi-plus-box</v-icon>
        </v-btn>
      </div>
      <div>
        <input id="active" v-model="selectedOption" type="radio" value="active" />
        <label for="active">Active</label>
        <input id="inactive" v-model="selectedOption" type="radio" value="inactive" />
        <label for="inactive">Inactive</label>
      </div>
    </form>
    <div>
      <button @click="save">บันทึก</button>
      <button @click="cancel">ยกเลิก</button>
      <button @click="back">กลับ</button>
    </div>
    <div v-if="showTable" class="datagrid">
      <table>
        <thead>
          <tr>
            <th>หัวข้อย่อ</th>
            <th>ชื่อหัวข้อย่อย</th>
            <th>คำอธิบาย</th>
            <th>สถานะ</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in items" :key="index">
            <td>{{ item.shortTitle }}</td>
            <td>{{ item.subTitle }}</td>
            <td>{{ item.description }}</td>
            <td>{{ item.status }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
  </div>
</template>

<script scoped>

export default {
  data() {
    return {
      shortTitle: '',
      subTitle: '',
      description: '',
      selectedOption: 'active',
      items: [],
      showTable: false
    }
  },
  methods: {
    submit() {
      if (!this.shortTitle || !this.subTitle || !this.description) {
        alert('กรุณากรอกข้อมูลให้ครบทุกช่อง')
        return
      }

      const newItem = {
        shortTitle: this.shortTitle,
        subTitle: this.subTitle,
        description: this.description,
        status: this.selectedOption
      }
      this.items.push(newItem)
      this.clearForm()
      this.showTable = true
    },
    cancel() {
      this.clearForm()
      this.clearTable()
      this.hideTable()
    },
    clearTable() {
      this.items = []
    },
    save() {
      // Code to save data goes here
    },
    clearForm() {
      this.shortTitle = ''
      this.subTitle = ''
      this.description = ''
      this.selectedOption = 'active'
    },
    hideTable() {
      this.showTable = false
    },
    back () {
      this.$router.push('/')
  },
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Kanit&display=swap');

.my-component {
  font-family: 'Kanit', sans-serif;
}

h2 {
  font-size: 24px;
  font-weight: bold;
  font-family: 'Kanit', sans-serif;
}

label {
  font-size: 18px;
  font-weight: bold;
  font-family: 'Kanit', sans-serif;
}

input[type="text"] {
  box-sizing: border-box;
  padding: 8px 12px;
  border-radius: 4px;
  border: 1px solid #ccc;
  font-size: 16px;
  width: 100%;
  margin-bottom: 10px;
  font-family: 'Kanit', sans-serif;
}

.my-icon {
  margin-bottom: 30px;
  color: #fff;
  font-family: 'Kanit', sans-serif;
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
}

button:hover {
  background-color: darkgreen;
}

table {
  border-collapse: collapse;
  margin-top: 20px;
  width: 100%;
}

th, td {
  border: 1px solid #ccc;
  padding: 8px;
  text-align: left;
  font-family: 'Kanit', sans-serif;
}

th {
  background-color: #ffffff;
  font-family: 'Kanit', sans-serif;
}

</style>
