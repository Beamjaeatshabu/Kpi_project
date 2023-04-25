
<template>
  <div class="center">
    <br>
    <div>
      <label for="abbrSelectBox">ชื่อนิติ (ชื่อย่อ): </label>
      <select id="abbrSelectBox" style="-webkit-appearance: listbox; -moz-appearance: listbox;">
        <option value="option1">ตัวเลือกที่ 1</option>
        <option value="option2">ตัวเลือกที่ 2</option>
      </select>
    </div>
    <br>
    <div>
      <label for="thNameSelectBox">ชื่อนิติบุคคลภาษาไทย: </label>
      <select id="thNameSelectBox" style="-webkit-appearance: listbox; -moz-appearance: listbox;">
        <option value="option1">ตัวเลือกที่ 1</option>
        <option value="option2">ตัวเลือกที่ 2</option>
      </select>
    </div>
    <br>
    <div class="container1">
      <div class="m">
        <label for="thNameSelectBox">เดือน</label>
        <select id="thNameSelectBox" style="-webkit-appearance: listbox; -moz-appearance: listbox;">
          <option value="01">มกราคม</option>
          <option value="02">กุมภาพันธ์</option>
          <option value="03">มีนาคม</option>
          <option value="04">เมษายน</option>
          <option value="05">พฤษภาคม</option>
          <option value="06">มิถุนายน</option>
          <option value="07">กรกฎาคม</option>
          <option value="08">สิงหาคม</option>
          <option value="09">กันยายน</option>
          <option value="10">ตุลาคม</option>
          <option value="11">พฤศจิกายน</option>
          <option value="12">ธันวาคม</option>
        </select>
      </div>
      <div class="q">
        <label for="thNameSelectBox">quarter</label>
        <select id="thNameSelectBox" style="-webkit-appearance: listbox; -moz-appearance: listbox;">
          <option value="Q1"> Q1</option>
          <option value="Q2"> Q2</option>
          <option value="Q3"> Q3</option>
          <option value="Q4"> Q4</option>
        </select>
      </div>
      <div class="y">
        <label for="thNameSelectBox">year</label>
        <select id="thNameSelectBox" style="-webkit-appearance: listbox; -moz-appearance: listbox;">
          <option value="option1">ตัวเลือกที่ 1</option>
          <option value="option2">ตัวเลือกที่ 2</option>
        </select>
      </div>
    </div>
    <br>
    <br>
    <form>
      <table>
        <thead>
          <th colspan="7" style="text-align:center;" id="q-select">
            <div class="select-wrapper">
              <select id="q-select" v-model="selectedQuarter"
                style="-webkit-appearance: listbox; -moz-appearance: listbox;">
                <option value="Q1"> Q1</option>
                <option value="Q2"> Q2</option>
                <option value="Q3"> Q3</option>
                <option value="Q4"> Q4</option>
              </select>
            </div>
          </th>
          <tr>
            <th rowspan="2">รายการประเมิน</th>
            <th rowspan="2" class="actual">น้ำหนัก</th>
            <th colspan="3">ผล</th>
            <th rowspan="2">target</th>
          </tr>
          <tr class="my-table-header">
            <th class="M1" v-if="selectedQuarter === 'Q1'">มกราคม </th>
            <th class="M1" v-if="selectedQuarter === 'Q1'">กุมภาพันธ์ </th>
            <th class="M1" v-if="selectedQuarter === 'Q1'">มีนาคม </th>
            <th class="M2" v-if="selectedQuarter === 'Q2'">เมษายน </th>
            <th class="M2" v-if="selectedQuarter === 'Q2'">พฤษภาคม</th>
            <th class="M2" v-if="selectedQuarter === 'Q2'">มิถุนายน </th>
            <th class="M3" v-if="selectedQuarter === 'Q3'">กรกฎาคม </th>
            <th class="M3" v-if="selectedQuarter === 'Q3'">สิงหาคม </th>
            <th class="M3" v-if="selectedQuarter === 'Q3'">กันยายน </th>
            <th class="M4" v-if="selectedQuarter === 'Q4'">ตุลาคม </th>
            <th class="M4" v-if="selectedQuarter === 'Q4'">พฤศจิกายน</th>
            <th class="M4" v-if="selectedQuarter === 'Q4'">ธันวาคม </th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td style="padding: 5px; text-align: left;">
              จำนวนครั้งการเกิด Break down
            </td>
            <td>น้ำหนัก 10</td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input2" name="num-input2" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input3" name="num-input3" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>
          <tr>
            <td style=" padding: 5px; text-align: left;">
              การจัดเก็บหนี้ประจำปี 2556
            </td>
            <td>น้ำหนัก 5</td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>
          <tr>
            <td style=" padding: 5px; text-align: left;">
              การจัดเก็บหนี้ต่ำกว่ามาตรฐานของหนี้ค้าง ณ วันปิดรอบงบนิติฯ
            </td>
            <td>น้ำหนัก 5</td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>
          <tr>
            <td style=" padding: 5px; text-align: left;">
              การจัดเก็บรายรับค่าชดเชยพื้นที่ส่วนกลางเป็นไปตามเงื่อนไขสัญญา
            </td>
            <td>น้ำหนัก 5</td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>

          <th colspan="6">การดำเนินงานของนิติเป็นไปตามกำหนด</th>

          <tr>
            <td style=" padding: 5px; text-align: left;">
              ระยะเวลาในการเปิดประชุมนับแต่เริ่มประชุม(นาที)
            </td>
            <td>น้ำหนัก 3</td>
            <td>
              <input type="number" id="num-input4" name="num-input4" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input5" name="num-input5" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input6" name="num-input6" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>
          <tr>
            <td style=" padding: 5px; text-align: left;">
              ความเข้าใจในการอพยพหนีไฟ
            </td>
            <td>น้ำหนัก 3</td>
            <td>
              <input type="number" id="num-input4" name="num-input4" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input5" name="num-input5" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input6" name="num-input6" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>
          <tr>
            <td style=" padding: 5px; text-align: left;">
              การจัดส่งเอกสารราชการเลยตามกำหนด ทส1,ทส 2, ร.1, สวล.
            </td>
            <td>น้ำหนัก 3</td>
            <td>
              <input type="number" id="num-input4" name="num-input4" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input5" name="num-input5" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input6" name="num-input6" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>

          <th colspan="6"></th>

          <tr>
            <td style=" padding: 5px; text-align: left;">
              ผลวิเคราะห์คุณภาพน้ำทิ้งไม่ผ่านเกณฑ์ (ผ่าน = 0 / ไม่ผ่าน =1)
            </td>
            <td>น้ำหนัก 5 </td>
            <td>
              <input type="number" id="num-input4" name="num-input4" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input5" name="num-input5" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input6" name="num-input6" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>
          <tr>
            <td style=" padding: 5px; text-align: left;">
              การคัดแยกขยะรีไซเคิล เทียบขยะทั้งหมด
            </td>
            <td> น้ำหนัก 5 </td>
            <td>
              <input type="text" placeholder="ปริมาณขยะทั้งหมด">
              <br>
              <br>
              <input type="text" placeholder="ปริมาณขยะรีไซต์เคิล">
              <br>
              <br>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>
          <tr>
            <td style=" padding: 5px; text-align: left;">
              จำนวนครั้งในการซักซ้อมเหตุฉุกเฉินของทีมงาน 1 ครั้ง / ไตรมาส
            </td>
            <td>น้ำหนัก 5 </td>
            <td>
              <input type="number" id="num-input4" name="num-input4" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input5" name="num-input5" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input6" name="num-input6" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>
          <tr>
            <td style=" padding: 5px; text-align: left;">
              ความพึงพอใจจากเจ้าของร่วม
            </td>
            <td>น้ำหนัก 7</td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="text" id="percent-input4" name="percent-input4" maxlength="3" placeholder="%">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>
          <tr>
            <td style=" padding: 5px; text-align: left;">
              ความพึงพอใจจากคณะกรรมการ
            </td>
            <td>น้ำหนัก 8</td>
            <td>
              <input type="number" id="num-input4" name="num-input4" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input5" name="num-input5" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input6" name="num-input6" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>

          <th colspan="7">ข้อร้องเรียน </th>

          <tr>
            <td style=" padding: 5px; text-align: left;">
              จำนวนข้อร้องเรียนเรื่อง Service Mind
            </td>
            <td>น้ำหนัก 3</td>
            <td>
              <input type="number" id="num-input4" name="num-input4" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input5" name="num-input5" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input6" name="num-input6" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>
          <tr>
            <td style=" padding: 5px; text-align: left;">
              ข้อร้องเรียนด้าน Service น้อยกว่าปี 2565
            </td>
            <td>น้ำหนัก 3</td>
            <td>
              <input type="number" id="num-input4" name="num-input4" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input5" name="num-input5" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input6" name="num-input6" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>
          <tr>
            <td style=" padding: 5px; text-align: left;">
              ผลการตรวจมาตรฐานการทำงานจาก QA ไม่ผ่านเกณฑ์
            </td>
            <td>น้ำหนัก 30</td>
            <td>
              <input type="text" placeholder="จน.ครั้งปี 64">
              <br>
              <br>
              <input type="number" id="num-input4" name="num-input4" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input5" name="num-input5" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input6" name="num-input6" max="50" maxlength="2">
            </td>
            <td>
              <input type="number" id="num-input1" name="num-input1" max="50" maxlength="2">
            </td>
          </tr>
          <th colspan="6"></th>
        </tbody>
      </table>
    </form>
    <br>
    <button class="cancle">ยกเลิก</button>
    <button class="submit">บันทึก</button>

  </div>
</template>
<style scoped>
div {
  margin-bottom: 10px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
  font-family: 'Kanit', sans-serif;
}

select {

  width: 100%;
  padding: 8px 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  font-family: 'Kanit', sans-serif;
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
  /* position: fixed; */
  background-color: #4CAF50;
  color: white;
}

input[type="number"],
input[type="text"] {
  width: 100%;
  margin: 8px 0;
  box-sizing: border-box;
  border-radius: 4px;
  background-color: #f2f2f2;
  border: 1px solid #1d1b1b;
  border-radius: 3px;
  color: #000000;
  /* เพิ่มโค้ดสีข้อความ */
  font-family: 'Kanit', sans-serif;
}


button {
  background-color: darkgreen;
  border: none;
  color: #fff;
  padding: 10px 20px;
  text-align: right;
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

.cancle {
  float: right;
}

.submit {
  float: right;
}


#q-select {
  width: 70px;
  /* ปรับขนาดของเลือก Q1-Q4 ให้คงที่ */
  text-align: center;
  color: rgb(255, 250, 250);
}

#q-select option {
  color: #000;
}

#q-select select {
  border: none;
}

tr.my-table-header>th {
  text-align: center;
  border: 1px solid #ddd;
  padding: 8px;
  font-family: 'Kanit', sans-serif;
}

.my-table-header th {
  text-align: center;
  border: 1px solid #ddd;
  padding: 8px;
  font-family: 'Kanit', sans-serif;
  background-color: #4CAF50;
  color: white;
}

.my-table-header td {
  width: 100px;
  text-align: center;
  border: 1px solid #ddd;
  padding: 8px;
  font-family: 'Kanit', sans-serif;
}
.M1 {
  width: 150px;
}
.M2 {
  width: 150px;
}
.M3 {
  width: 150px;
}
.M4 {
  width: 150px;
}
.actual {
  width: 150px;
}

tbody tr:nth-child(even) {
  background-color: #f2f2f2;
}

tbody tr:hover {
  background-color: #ddd;
}

.container1 {
  display: grid;
  grid-template-columns: auto auto;
  /* แบ่ง column เป็นสองส่วน */
  gap: 10px;
  /* เว้นระยะห่างระหว่างสอง element */
}


.m,
.q,
.y {
  grid-row: 1;
  /* ให้ทั้งสาม element อยู่ใน row เดียวกัน */
}
</style>

<script scoped>

export default {
  data() {
    return {
      selectedQuarter: "Q1",
    };
  },
};

</script>