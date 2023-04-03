<template>
  <div class="container">
    <div>
    <h2>หัวข้อหลักการประเมิน</h2>
    <div class="select-wrapper">
 <i class="mdi mdi-menu-down"></i>
<select v-model="selectedItem">
  <option disabled value="">-- โปรดเลือกรายการ --</option>
  <option v-for="item in items" :key="item.value" :value="item.value">{{ item.label }}</option>
</select>

</div>
    <div>
      <label class="label" for="evaluation-title">หัวข้อประเมิน</label>
      <input
        id="evaluation-title"
        v-model="evaluationTitle"
        class="input"
        type="text"
        name="evaluation-title"
      />
    </div>
    
    <div>
      <h2>เกณฑ์การประเมิน</h2>
      <div>
        <i class="mdi mdi-menu-down"></i>
        <label for="evaluation-level">เลือกระดับการประเมิน:</label>
        <select
          id="evaluation-level"
          v-model="selectedLevel"
          name="evaluation-level"
        >
        
          <option disabled value=""
            >-- โปรดเลือกระดับการประเมิน --</option
          >
          <option
            v-for="(level, index) in evaluationLevels"
            :key="index"
            :value="level"
          >
            {{ level }}
          </option>
        </select>
        
      </div>
      <div>
        <label for="evaluation-comment">ความคิดเห็น:</label>
        <input
          id="evaluation-comment"
          v-model="comment"
          type="text"
          name="evaluation-comment"
        />
      </div>
    </div>
      <button @click="submit">ส่งเกณฑ์การประเมิน</button>
      <button @click="save">บันทึกข้อมูล</button>
      <button @click="cancel">ยกเลิก</button>
      <button @click="back">กลับ</button>
    </div>
    <table v-if="showResult">
      <thead>
        <tr>
          <th>รายการ</th>
          <th>หัวข้อประเมิน</th>
          <th>ระดับการประเมิน</th>
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
    evaluationLevels: ["ดีมาก", "ดี", "พอใช้", "แย่"],
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
      alert("ไม่มีข้อมูลให้บันทึก");
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
  back () {
      this.$router.push('/')
  },
},
};
</script>


<style scoped>
/* div .container {
  margin: 0 auto;
  max-width: 600px;
  padding: 20px;
  border: 1px solid #ccc;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.3);
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
} */
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
  width: 100%;
  padding: 12px;
  border-radius: 8px;
  border: 1px solid #ccc;
  margin-bottom: 24px;
  font-size: 18px;
}

/* กำหนดรูปแบบช่องกรอกข้อมูล */
.input  {
  width: 100%;
  padding: 12px;
  border-radius: 8px;
  border: 1px solid #ccc;
  margin-bottom: 24px;
  font-size: 18px;
}

#evaluation-comment {
  width: 100%;
  padding: 12px;
  border-radius: 8px;
  border: 1px solid #ccc;
  margin-bottom: 24px;
  font-size: 18px;
}

label[for="evaluation-comment"] {
  font-size: 18px;
  font-weight: bold;
  display: block;
  margin-bottom: 12px;
}

/* กำหนดรูปแบบปุ่ม
button {
  background-color: #4caf50;
  color: #fff;
  border-radius: 8px;
  border: none;
  padding: 12px 24px;
  font-size: 18px;
  cursor: pointer;
  margin-right: 12px;
} */

/* กำหนดรูปแบบตาราง */
table {
  border-collapse: collapse;
  width: 100%;
}

th,
td {
  text-align: left;
  padding: 8px;
  border-bottom: 1px solid #ddd;
}

th {
  background-color: #f2f2f2;
}

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
}
button {
background-color: darkgreen;
border: none;
color: white;
padding: 12px 24px;
text-align: center;
text-decoration: none;
display: inline-block;
font-size: 16px;
margin: 4px 2px;
cursor: pointer;
transition: background-color 0.3s ease, transform 0.3s ease; /* เพิ่ม transition สำหรับเปลี่ยนสีพื้นหลัง */
}

button:hover {
background-color: darkgreen;
}

button:active {
background-color: #3d99a1;
transform: translateY(2px);
}
.mdi {
  float: right;
}
</style>




