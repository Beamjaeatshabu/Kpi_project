<template>
  <div class="container">
    <div>
      <form>
        <div>
          <label for="short-title">หัวข้อย่อย:</label>
          <input id="short-title" v-model="shortTitle" type="text" />
        </div>
        <div>
          <label for="sub-title">ชื่อหัวข้อย่อย:</label>
          <input id="sub-title" v-model="subTitle" type="text" />
        </div>
        <div>
          <label for="description">คำอธิบาย:</label>
          <textarea input id="description" v-model="description" type="text"></textarea>
          <div>
            <input id="active" v-model="selectedOption" type="radio" value="active" />
            <label for="active">Active</label>
            <input id="inactive" v-model="selectedOption" type="radio" value="inactive" />
            <label for="inactive">Inactive</label>
          </div>
          <div class="button-container">
            <v-btn icon @click="submit">
              <v-icon  style="color: white; width: 30px; height: 20px;" >mdi-plus-box</v-icon>
            </v-btn>
            <p v-if="!showTable && !shortTitle && !subTitle && !description" class="warn">กรุณากดเครื่องหมาย +
              เพื่อแสดงข้อมูลในตาราง</p>
          </div>
        </div>

      </form>
      <div>
        <button @click="back" class="back">กลับ</button>
        <button @click="cancel" class="cancel">ยกเลิก</button>
        <button @click="save" class="save">บันทึก</button>
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
  middleware: 'auth',
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
        return;
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
      if (!this.showTable) {
        alert('กรุณากดเครื่องหมาย + เพื่อแสดงข้อมูลในตาราง')
        return;
      }

      // Code to save data goes here
      alert("บันทึกข้อมูลสำเร็จ");
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
    back() {
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
textarea {
  width: 100%;
  height: 150px;
  padding: 12px 20px;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
  resize: none;
}



.button-container {
  display: flex;
  align-items: center;
}


.warn {
  display: none;
  color: red;
  margin: 0;
}

.show {
  display: block;
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

.cancel {
  float: right;
}

.save {
  float: right;
}

.back {
  float: right;
}

table {
  border-collapse: collapse;
  width: 100%;
  font-family: 'Kanit', sans-serif;
}

th,
td {
  text-align: center;
  border: 1px solid #ddd;
  padding: 8px;
  font-family: 'Kanit', sans-serif;
}

th {
  background-color: #4CAF50;
  color: white;
}

tbody tr:nth-child(even) {
  background-color: #f2f2f2;
}

tbody tr:hover {
  background-color: #ddd;
}
</style>
