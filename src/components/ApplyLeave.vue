<template>
  <h1>{{ leave }}</h1>
<div class="container py-4">
  <div class="card shadow-sm w-75 mx-auto">
  <div class="input-group mb-3  w-50 mx-auto">
    <span class="input-group-text" id="basic-addon1">Name</span>
    <input
      type="text"
      class="form-control"
      placeholder="Full Name"
      aria-label="fullName"
      aria-describedby="basic-addon1"
      v-model="fullName"
    />
  </div>

  <div class="input-group mb-3 w-50 mx-auto">
    <span class="input-group-text" id="basic-addon2">Emp ID</span>
    <input
      type="text"
      class="form-control"
      placeholder="Your Employee ID"
      aria-label="empId"
      aria-describedby="basic-addon2"
      v-model="empId"
    />
  </div>

  <div class="mb-3 w-50 mx-auto">
    <label for="startDate" class="form-label"><strong>Choose Start Date:</strong></label>
    <input type="date" class="form-control" id="startDate" min="2026-04-01" v-model="startDate" />
  </div>

  <div class="mb-3 w-50 mx-auto">
    <label for="startDate" class="form-label"><strong>Choose End Date:</strong></label>
    <input type="date" class="form-control" id="endDate" max="2026-12-31" v-model="endDate"/>
  </div>

  <div class="leaveType">
    <div class="dropdown">
      <button
        class="btn btn-secondary dropdown-toggle"
        type="button"
        data-bs-toggle="dropdown"
        aria-expanded="false"
      >
        {{SelectedLeave ||'Type of Leave'}}
      </button>
      <ul class="dropdown-menu">
        <li>
          <button class="dropdown-item" type="button" @click="selectLeave('Annual Leave')">Annual Leave</button>
        </li>
        <li>
          <button class="dropdown-item" type="button" @click="selectLeave('Family Responsibility')">
            Family Responsibility
          </button>
        </li>
        <li>
          <button class="dropdown-item" type="button" @click="selectLeave('Paid Sick Leave')">Paid Sick Leave</button>
        </li>
        <li>
          <button class="dropdown-item" type="button" @click="selectLeave('Leave Without Pay')">Leave Without Pay</button>
        </li>
        <li>
          <button class="dropdown-item" type="button" @click="selectLeave('Emergency Leave')">Emergency Leave</button>
        </li>
        <li>
          <button class="dropdown-item" type="button" @click="selectLeave('Maternity Leave')">Maternity Leave</button>
        </li>
      </ul>
    </div>
    <label for="leaveType" class="label">Leave selected: {{ selectedLeave || 'None'}}</label>
  </div>

  <div class="d-grid gap-2 col-6 mx-auto">
    <button class="btn btn-primary" type="button" >Submit Leave Request</button>
  </div>
</div>
</div>
</template>

<script>
export default {
  name: "ApplyLeave",
  props: {
    leave: String,
  },
  data(){
    return{  //components to store our inputs 
      selectedLeave:'',
      fullName:'',
      empId: '',
      startDate:'',
      endDate:''
    
    };
  },
  methods:{
    selectLeave(type){
      this.selectedLeave = type; //object to store leave from dropdown selection 
    },
  }
};
</script>

<style scoped>
.label{
  margin-bottom: 2%;
}

button{
  margin-bottom: 2%;
}
</style>
