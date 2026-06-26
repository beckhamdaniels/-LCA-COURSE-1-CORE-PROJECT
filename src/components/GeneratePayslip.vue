<template>
  <h1>{{ payslip }}</h1>
<div class="container py-4">  
 <div class="card shadow-sm w-75 mx-auto">

 <div class="input-group mb-3 p-3">
  <input type="file" class="form-control" id="inputGroupFile02">
  <label class="input-group-text" for="inputGroupFile02" :fileUpload>Upload</label>
</div>

  <div class="dropdown ">
    <button
      class="btn btn-info dropdown-toggle"
      type="button"
      data-bs-toggle="dropdown"
      aria-expanded="false"
    >
      {{ selectedMonth || "Month" }}
    </button>
    <ul class="dropdown-menu">
      <li>
        <button
          class="dropdown-item"
          type="button"
          @click="selectMonth('January')"
        >
          January
        </button>
      </li>
      <li>
        <button
          class="dropdown-item"
          type="button"
          @click="selectMonth('Febuary')"
        >
          Febuary
        </button>
      </li>
      <li>
        <button
          class="dropdown-item"
          type="button"
          @click="selectMonth('March')"
        >
          March
        </button>
      </li>
      <li>
        <button
          class="dropdown-item"
          type="button"
          @click="selectMonth('April')"
        >
          April
        </button>
      </li>
      <li>
        <button class="dropdown-item" type="button" @click="selectMonth('May')">
          May
        </button>
      </li>
      <li>
        <button
          class="dropdown-item"
          type="button"
          @click="selectMonth('June')"
        >
          June
        </button>
      </li>
      <li>
        <button
          class="dropdown-item"
          type="button"
          @click="selectMonth('July')"
        >
          July
        </button>
      </li>
      <li>
        <button
          class="dropdown-item"
          type="button"
          @click="selectMonth('August')"
        >
          August
        </button>
      </li>
      <li>
        <button
          class="dropdown-item"
          type="button"
          @click="selectMonth('September')"
        >
          September
        </button>
      </li>
      <li>
        <button
          class="dropdown-item"
          type="button"
          @click="selectMonth('October')"
        >
          October
        </button>
      </li>
      <li>
        <button
          class="dropdown-item"
          type="button"
          @click="selectMonth('November')"
        >
          November
        </button>
      </li>
      <li>
        <button
          class="dropdown-item"
          type="button"
          @click="selectMonth('December')"
        >
          December
        </button>
      </li>
    </ul>
  </div>

  <button type="button" class="btn btn-success " @click='success'>Upload Payroll</button>
 </div>
</div>
</template>

<script>
export default {
  name: "GeneratePayslip",
  props: {
    payslip: String,
  },
  data() {
    return {
      selectedMonth: "",
      fileUpload: "",
      employees: [],
    };
  },
  methods: {
    selectMonth(type){
      this.selectedMonth = type
    },
    success(){
      if(
        this.selectedMonth === ''||
        this.fileUpload === ''
      ){
        alert('Leave Request unsuccessful, Please fill in the correct fields')
      }else {
        alert(`Leave request submitted successfully for ${this.fullName}!`)
      }
    }
  },
};
</script>

<style scoped>
button {
  margin-bottom: 2%;
}

</style>
