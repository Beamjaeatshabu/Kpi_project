<template>
  <div class="container">
    <h1 style="font-family:'Kanit', sans-serif;">กำหนดกลุ่มหัวข้อการประเมิน</h1>
    <div class="long-line"></div>

    <br>
    <span>ปี :</span>
    <select style="-webkit-appearance: listbox; -moz-appearance: listbox;">
      <option value="01"> </option>
    </select>


    <span>เดือน :</span>
    <select style="-webkit-appearance: listbox; -moz-appearance: listbox;">
      <option value="01"> </option>
    </select>


    <span>โครงการ :</span>
    <select style="-webkit-appearance: listbox; -moz-appearance: listbox;">
      <option value="01"> </option>
    </select>

    <router-link to="/kpiyear" target="_blank">
      <button>(F) Facility Management : การบริหารจัดการทรัพย์ส่วนกลาง</button>
    </router-link>
    <router-link to="/kpiyear" target="_blank">
      <button>(A) Activity Management : การบริหารจัดการกิจกรรม</button>
    </router-link>
    <router-link to="/kpiyear" target="_blank">
      <button>(L) Life Quality and Legal Management : การบริหารจัดการคุณภาพชีวิตและกฏหมายกำหนด</button>
    </router-link>
    <router-link to="/kpiyear" target="_blank">
      <button>(E) Environment Management: การบริหารจัดการสิ่งแวดล้อม</button>
    </router-link>
    <router-link to="/kpiyear" target="_blank">
      <button>(B) Budgeting Management :การบริหารจัดการงบประมาณ</button>
    </router-link>
    <router-link to="/kpiyear" target="_blank">
      <button>(P) People Management : การบริหารจัดการผู้ที่เกี่ยวข้อง</button>
    </router-link>
  </div>
</template>
<style scoped>
.long-line {
  border-top: 2px solid #ddd;
  /* เส้นแนวนอนสีเทาเข้ม */
  height: 1px;
  /* ความสูงของเส้นแนวนอน */
  width: 100%;
  /* กว้างเท่ากับขนาดของ container */
}

span {
  margin-bottom: 5px;
  font-weight: bold;
  font-family: 'Kanit', sans-serif;
}

button {
  width: 100%;
  border-radius: 4px;
  padding: 10px 20px;
  background-color: rgb(173, 175, 173);
  border: none;
  color: #000000;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
  font-family: 'Kanit', sans-serif;
  border-radius: 4px;
  margin-right: 10px;
  margin-bottom: 20px;
  box-shadow: 0px 5px 10px rgba(0,0,0,0.3);
}

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
@media (max-width: 767px) {
  span {
  margin-bottom: 5px;
  font-weight: bold;
  font-family: 'Kanit', sans-serif;
}
select {
  box-sizing: border-box;
  padding: 2px 10px;
  border-radius: 4px;
  border: 1px solid #ccc;
  font-size: 16px;
  width: 19%;
  margin-bottom: 10px;
  font-family: 'Kanit', sans-serif;
}

}
</style>