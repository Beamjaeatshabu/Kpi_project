<template>
    <div class="container" >
        <span>ปี :</span>
        <select style="-webkit-appearance: listbox; -moz-appearance: listbox;">
            <option> 1 </option>
        </select>
        <span>เดือน :</span>
        <select style="-webkit-appearance: listbox; -moz-appearance: listbox;">
            <option> 1 </option>
        </select>
        <span>โครงการ :</span>
        <select >
            <option> 1 </option>
        </select>
        <div class="long-line"></div>
        <br>
        <form>
            <table>
                <thead>
                    <tr>
                        <th>หมวด</th>
                        <th>ลำดับ</th>
                        <th>หัวข้อ</th>
                        <th>เป้า(Target)</th>
                        <th>เดือน</th>
                        <th>ผล(Actual)/2565</th>
                        <th class="ac2">ผล(Actual)/2566</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>F</td>
                        <td>1</td>
                        <td>จำนวนครั้งของการเกิด Breakdown ของเครื่องจักรหลักในระบบหลัก </td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                    </tr>
                    <tr>
                        <td>B</td>
                        <td>1</td>
                        <td>% การดำเนินการเป็นไปตามกฎหมายกำหนด </td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                    </tr>
                    <tr>
                        <td>B</td>
                        <td>2</td>
                        <td>% การจัดเก็บหนี้ประจำปี 2566</td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                    </tr>
                    <tr>
                        <td>B</td>
                        <td>3</td>
                        <td>% การจัดเก็บหนี้ต่ำกว่ามาตรฐานของหนี้ค้าง ณ รอบงบประมาณของนิติฯ </td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                    </tr>
                    <tr>
                        <td>B</td>
                        <td>4</td>
                        <td>%การเก็บรายรับค่าชดเชยพื้นที่ส่วนกลาง 100% (แจ้งหนี้ + จัดเก็บไปไปตามระยะเวลาเป็นไปตามเงื่อนไขที่กำหนด)</td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                        <td><input type="text"></td>
                    </tr>
                </tbody>
            </table>
        </form>
        <br>
        <router-link to="/regularyear">
            <button>กลับ</button>
        </router-link>
    </div>
</template>
<style scoped>
select {
  box-sizing: border-box;
  padding: 2px 10px;
  border-radius: 4px;
  border: 1px solid #ccc;
  font-size: 16px;
  width: 25%;
  margin-bottom: 10px;
  font-family: 'Kanit', sans-serif;
}
table {
    background-color: #007033;
    border-collapse: collapse;
    width: 100%;
    font-family: 'Kanit', sans-serif;
}

th,
td {
    text-align: center;
    border: 1px solid #ffffff;
    padding: 8px;
    font-family: 'Kanit', sans-serif;
}

th {
    /* position: fixed; */
    color: rgb(252, 252, 252);
}
th, td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}

tbody tr:nth-child(even) {
  background-color: #f2f2f2;
}

tbody tr:nth-child(odd) {
  background-color: #e6e6e6;
}
.ac2{
    background-color: #F7941D;
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
    float: right;
}

button:hover {
    background-color: darkgreen;
}
.long-line {
  border-top: 2px solid #ddd;
  /* เส้นแนวนอนสีเทาเข้ม */
  height: 1px;
  /* ความสูงของเส้นแนวนอน */
  width: 100%;
  /* กว้างเท่ากับขนาดของ container */
}
</style>