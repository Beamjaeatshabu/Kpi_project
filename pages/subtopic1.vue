<template>
  <div class="container">
    <h1 style="font-family:'Kanit', sans-serif;">กำหนดหัวย่อยการประเมิน</h1>
    <div class="long-line"></div>
    <br>
        <form>   
          <label for="evaluation-level">หัวข้อหลักประเมิน :</label>
        <select id="evaluation-level" class="main1" v-model="selectedLevel" name="evaluation-level"
          style="-webkit-appearance: listbox; -moz-appearance: listbox;">
          <option disabled value="">-- โปรดเลือกระดับการประเมิน --</option>
          <option v-for="(level, index) in evaluationLevels" :key="index" :value="level">{{ level }}</option>
        </select>
          <div>
            <label for="short-title">หัวข้อประเมิน :</label>
            <input id="short-title" v-model="shortTitle" type="text" />
          </div>
          <div>
            <label for="sub-title">ชื่อข้อประเมิน :</label>
            <input id="sub-title" v-model="subTitle" type="text" />
          </div>
          <div>
            <label for="description">คำอธิบาย :</label>
            <textarea input id="description" v-model="description" type="text"></textarea>
            <br>
            <br>
            <div class="radio">
              <input id="active" v-model="selectedOption" type="radio" value="active" />
              <label for="active">Active</label>
              <input id="inactive" v-model="selectedOption" type="radio" value="inactive" />
              <label for="inactive">Inactive</label>
            </div>
            <br>
            <v-btn icon @click="submit"
              style="margin:-50px; margin-left:initial; position: relative; right: -200px; top: -62px;">
              <v-icon style="color: white; width: 30px; height: 20px;  margin: 0px;">mdi-plus-box</v-icon>
            </v-btn>
            <div class="button-container">
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

#evaluation-level {
  box-sizing: border-box;
  padding: 8px 12px;
  border-radius: 4px;
  border: 1px solid #ccc;
  font-size: 16px;
  width: 80%;
  margin-bottom: 10px;
  font-family: 'Kanit', sans-serif;
  position: relative;
  left: 10px;
}

input[type="text"] {
  box-sizing: border-box;
  padding: 8px 12px;
  border-radius: 4px;
  border: 1px solid #ccc;
  font-size: 16px;
  width: 80%;
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

.button-container {
  display: flex;
  align-items: center;
}

.radio {
  border: 1px solid #ccc;
  padding: 10px;
  background-color: #ccc;
  border-radius: 5px;
  width: 190px;
  height: 50px;
  position: relative;
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

.long-line {
  border-top: 2px solid #ddd;
  /* เส้นแนวนอนสีเทาเข้ม */
  height: 1px;
  /* ความสูงของเส้นแนวนอน */
  width: 100%;
  /* กว้างเท่ากับขนาดของ container */
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
@media (max-width: 767px) {
  #evaluation-level {
  box-sizing: border-box;
  padding: 8px 12px;
  border-radius: 4px;
  border: 1px solid #ccc;
  font-size: 16px;
  width: 50%;
  margin-bottom: 10px;
  font-family: 'Kanit', sans-serif;
  position: relative;
  left: 0px;
}

input[type="text"] {
  box-sizing: border-box;
  padding: 8px 12px;
  border-radius: 4px;
  border: 1px solid #ccc;
  font-size: 16px;
  width: 50%;
  position: relative;
  left: 30px;
  margin-bottom: 10px;
  font-family: 'Kanit', sans-serif;
}
}
</style>
