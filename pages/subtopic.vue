<template>
  <div class="container">
    <div>
      <h2>หัวข้อหลักการประเมิน</h2>
      <div class="select-wrapper">
        <label for="evaluation-level">หัวข้อหลักการประเมิน:</label>
        <select v-model="selectedItem" style="-webkit-appearance: listbox; -moz-appearance: listbox;">
          <option disabled value="">-- โปรดเลือกรายการ --</option>
          <option v-for="item in items" :key="item.value" :value="item.value">{{ item.label }}</option>
        </select>
      </div>

      <div>
        <label class="label" for="evaluation-title">หัวข้อประเมิน:</label>
        <input id="evaluation-title" v-model="evaluationTitle" class="input" type="text" name="evaluation-title" />
      </div>

      <div>
        <h2>เกณฑ์การประเมิน</h2>
        <label for="evaluation-level">เลือกระดับการประเมิน:</label>
        <div class="container1">
          <select id="evaluation-level" class="main1" v-model="selectedLevel" name="evaluation-level" style="-webkit-appearance: listbox; -moz-appearance: listbox;">
            <option disabled value="">-- โปรดเลือกระดับการประเมิน --</option>
            <option v-for="(level, index) in evaluationLevels" :key="index" :value="level">{{ level }}</option>
          </select>
          <label for="evaluation-comment"> </label>
          <input class="comment1" id="evaluation-comment" v-model="comment" type="text" name="evaluation-comment"></input>
        </div>
      </div>

      <button class="click" @click="back">กลับ</button>
      <button class="click" @click="cancel">ยกเลิก</button>
      <button class="click" @click="save">บันทึกข้อมูล</button>
      <button class="click" @click="submit">เพิ่ม</button>
    </div>

    <table v-if="showResult">
      <thead>
        <tr>
          <th>หัวข้อที่</th>
          <th>หัวข้อประเมิน</th>
          <th>เกณฑ์การประเมิน</th>
          <!-- <th>ความคิดเห็น</th> -->
        </tr>
      </thead>
      <tbody>
        <tr v-for="(evaluation, index) in evaluations" :key="index">
          <td>{{ evaluation.selectedItem }}</td>
          <td>{{ evaluation.evaluationTitle }}</td>
          <td>{{ evaluation.selectedLevel }}</td>
          <!-- <td>{{ evaluation.comment }}</td> -->
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script scoped>
export default {
  data() {
    return {
      selectedItem: "",
      items: [
        { label: "รายการที่ 1", value: "1" },
        { label: "รายการที่ 2", value: "2" },
        { label: "รายการที่ 3", value: "3" },
      ],
      evaluationTitle: "",
      selectedLevel: "",
      evaluationLevels: ["<>", "≥", "≠"],
      comment: "",
      evaluations: [],
      showResult: false,
    };
  },
  methods: {
    submit() {
      if (
        this.selectedItem === "" ||
        this.evaluationTitle === "" ||
        this.selectedLevel === ""
      ) {
        alert("กรุณากรอกข้อมูลให้ครบทุกช่อง");
        return;
      }
      const evaluation = {
        selectedItem: this.selectedItem,
        evaluationTitle: this.evaluationTitle,
        selectedLevel: this.selectedLevel,
        comment: this.comment, // เพิ่ม comment ที่หายไป
      };
      this.evaluations.push(evaluation);
      this.selectedItem = "";
      this.evaluationTitle = "";
      this.selectedLevel = "";
      this.comment = "";
      this.showResult = true;
    },
    save() {
      if (this.evaluations.length === 0) {
        alert("ไม่มีข้อมูลบันทึก");
        return;
      }
      alert("บันทึกข้อมูลสำเร็จ");
      this.showData();
    },
    showData() {
      if (this.evaluations.length === 0) {
        alert("ไม่มีข้อมูลที่บันทึก");
      } else {
        // eslint-disable-next-line no-console
        console.log(this.evaluations);
      }
    },
    cancel() {
      this.selectedItem = "";
      this.evaluationTitle = "";
      this.selectedLevel = "";
      this.comment = "";
      this.evaluations = [];
      this.showResult = false;
    },
    back() {
      this.$router.push('/')
    },
  },
};
</script>

<style scoped>
/* กำหนดฟอนต์ให้กับตัวอักษรทั้งหมด */
* {
  font-family: 'Kanit', sans-serif;
}

/* กำหนดขนาดฟอนต์และรูปแบบของข้อความ */
h2 {
  font-size: 24px;
  font-weight: bold;
}

label {
  font-size: 18px;
  font-weight: bold;
}

/* กำหนดรูปแบบเลือกตัวเลือก */
select {
  box-sizing: border-box;
  padding: 8px 12px;
  border-radius: 4px;
  border: 1px solid #ccc;
  font-size: 16px;
  width: 100%;
  margin-bottom: 10px;
  font-family: 'Kanit', sans-serif;
}

/* กำหนดรูปแบบช่องกรอกข้อมูล */
input {
  box-sizing: border-box;
  padding: 8px 12px;
  border-radius: 4px;
  border: 1px solid #ccc;
  font-size: 16px;
  width: 100%;
  margin-bottom: 10px;
  font-family: 'Kanit', sans-serif;
}

#evaluation-comment {
  box-sizing: border-box;
  padding: 8px 12px;
  border-radius: 4px;
  border: 1px solid #ccc;
  font-size: 16px;
  width: 100%;
  margin-bottom: 10px;
  font-family: 'Kanit', sans-serif;
}

.container1 {
  display: grid;
  grid-template-columns: auto auto;
  /* แบ่ง column เป็นสองส่วน */
  gap: 10px;
  /* เว้นระยะห่างระหว่างสอง element */
}

#evaluation-level,
#evaluation-comment {
  grid-row: 1;
  /* ให้ทั้งสอง element อยู่ใน row เดียวกัน */
}



label[for="evaluation-comment"] {
  font-size: 18px;
  font-weight: bold;
  display: block;
  margin-bottom: 12px;
}

/* กำหนดรูปแบบปุ่ม */
button {
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  border-radius: 4px;
  margin-right: 10px;
  margin-bottom: 20px;
  cursor: pointer;
  background-color: darkgreen;
  border: none;
  color: white;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

button:hover {
  background-color: darkgreen;
}

button:active {
  background-color: #3d99a1;
  transform: translateY(2px);
}

.click {
  float: right;
}

/* กำหนดรูปแบบตาราง */
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

/* ย้ายไอคอนแสดงผลจากขวาไปซ้าย */
.mdi {
  float: left;
}
</style>
