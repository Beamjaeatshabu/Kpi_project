
<template>
  <div class="center">
    <br>
    <div>
      <label for="abbrSelectBox">ชื่อนิติ (ชื่อย่อ)▼: </label>
      <select id="abbrSelectBox">
        <option value="option1">ตัวเลือกที่ 1</option>
        <option value="option2">ตัวเลือกที่ 2</option>
      </select>
    </div>
    <br>
    <div>
      <label for="thNameSelectBox">ชื่อนิติบุคคลภาษาไทย▼: </label>
      <select id="thNameSelectBox">
        <option value="option1">ตัวเลือกที่ 1</option>
        <option value="option2">ตัวเลือกที่ 2</option>
      </select>
    </div>
    <br>
    <br>
    <form>
      <table>
        <thead>
        <th colspan="5" style="text-align:center;" id="q-select" > 
          <div class="select-wrapper">
            <select id="q-select" v-model="selectedQuarter" style="-webkit-appearance: listbox; -moz-appearance: listbox;">
              <option value="Q1"> Q1</option>
              <option value="Q2"> Q2</option>
              <option value="Q3"> Q3</option>
              <option value="Q4"> Q4</option>
            </select>
          </div>
        </th>
        <tr>
          <th>รายการการประเมิน</th>
          <th v-if="selectedQuarter === 'Q1'">มกราคม</th>
          <th v-if="selectedQuarter === 'Q1'">กุมภาพันธุ์</th>
          <th v-if="selectedQuarter === 'Q1'">มีนาคม</th>
          <th v-if="selectedQuarter === 'Q2'">เมษายน</th>
          <th v-if="selectedQuarter === 'Q2'">พฤษภาคม</th>
          <th v-if="selectedQuarter === 'Q2'">มิถุนายน</th>
          <th v-if="selectedQuarter === 'Q3'">กรกฎาคม</th>
          <th v-if="selectedQuarter === 'Q3'">สิงหาคม</th>
          <th v-if="selectedQuarter === 'Q3'">กันยายน</th>
          <th v-if="selectedQuarter === 'Q4'">ตุลาคม</th>
          <th v-if="selectedQuarter === 'Q4'">พฤศจิกายน</th>
          <th v-if="selectedQuarter === 'Q4'">ธันวาคม</th>
          <th>target</th>
        </tr>
      </thead>
        <tbody>
          <tr>
            <td style="padding: 5px; text-align: left;">
              จำนวนครั้งการเกิด Break down <span>(น้ำหนัก 10)</span>
            </td>

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
              การจัดเก็บหนี้ประจำปี 2556 <span>(น้ำหนัก 5)</span>
            </td>
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
              การจัดเก็บหนี้ต่ำกว่ามาตรฐานของหนี้ค้าง ณ วันปิดรอบงบนิติฯ <span>(น้ำหนัก 5)</span>
            </td>
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
              การจัดเก็บรายรับค่าชดเชยพื้นที่ส่วนกลางเป็นไปตามเงื่อนไขสัญญา<span>(น้ำหนัก 5)</span>
            </td>
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
              ระยะเวลาในการเปิดประชุมนับแต่เริ่มประชุม(นาที) <span>(น้ำหนัก 3)</span>
            </td>
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
              ความเข้าใจในการอพยพหนีไฟ (ผ่านแบบสอบถาม) <span>(น้ำหนัก 3)</span>
            </td>
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
          <tr>
          </tr>
          <tr> 
          <td style=" padding: 5px; text-align: left;">
            การจัดส่งเอกสารราชการเลยตามกำหนด ทส1,ทส 2, ร.1, สวล. <span>(น้ำหนัก 3)</span>
          </td>
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
              ผลวิเคราะห์คุณภาพน้ำทิ้งไม่ผ่านเกณฑ์ (ผ่าน = 0 / ไม่ผ่าน =1) <span>(น้ำหนัก 5)</span>
            </td>
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
              การคัดแยกขยะรีไซต์เคิลเทียบขยะทั้งหมด <span>(น้ำหนัก 5)</span>
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
              จำนวนครั้งในการซักซ้อมเหตุฉุกเฉินของทีมงาน 1 ครั้ง / ไตรมาส <span>(น้ำหนัก 5)</span>
            </td>
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
              ความพึงพอใจจากเจ้าของร่วม <span>(น้ำหนัก 7)</span>
            </td>
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
              ความพึงพอใจจากคณะกรรมการ <span>(น้ำหนัก 8)</span>
            </td>
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
        
            <th colspan="5">ข้อร้องเรียน </th>
        
          <tr>
            <td style=" padding: 5px; text-align: left;">
              จำนวนข้อร้องเรียนเรื่อง Service Miand <span>(น้ำหนัก 3)</span>
            </td>
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
              ข้อร้องเรียนด้าน Service น้อยกว่าปี 2565 <span>(น้ำหนัก 3)</span>
            </td>

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
              ผลการตรวจมาตรฐานการทำงานจาก QA ไม่ผ่านเกณฑ์ <span>(น้ำหนัก 30)</span>
            </td>
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
    <button class="submit">ยืนยัน</button>
    <button class="cancle">ยกเลิก</button>
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
  background-color: #4CAF50;
  color: white;
}

tbody tr:nth-child(even) {
  background-color: #f2f2f2;
}

tbody tr:hover {
  background-color: #ddd;
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
color: #000000; /* เพิ่มโค้ดสีข้อความ */
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

#q-select {
    text-align: center;
    color: rgb(255, 250, 250);
  }
  #q-select option {
  color: #000;
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