<template>
  <h1>{{ uploadPayroll }}</h1>
<div class="container py-4">
<div class="card shadow-sm w-75 mx-auto">
  <div class="input-group input-group-sm mb-3 w-25 p-3 mx-auto" id="empID">
    <span class="input-group-text" id="basic-addon2">Emp ID</span>
    <input
      type="text"
      class="form-control"
      placeholder="Your Employee ID"
      aria-label="empId"
      aria-describedby="basic-addon2"
      v-model="employeeId"
    />
  </div>

  <div class="mb-3">
    <label class="form-label font-weight-bold">Select Department:</label>
    <select
      class="form-select"
      v-model="selectedDepartment"
      @change="selectedRole = ''"
    >
      <option value="">-- Choose Department --</option>
      <option value="Development">Development</option>
      <option value="Design">Design</option>
      <option value="Marketing">Marketing</option>
      <option value="HR">HR</option>
      <option value="Finance">Finance</option>
      <option value="Support">Support</option>
      <option value="Security">Security</option>
      <option value="Product">Product</option>
    </select>
  </div>

  <div class="mb-3" v-if="filteredRoles.length > 0">
    <label class="form-label d-block font-weight-bold">Available Roles:</label>

    <div
      class="form-check-width: 1em"
      v-for="item in filteredRoles"
      :key="item.id"
    >
      <input
        class="form-check-input"
        type="radio"
        :id="'role-' + item.id"
        :value="item.role"
        v-model="selectedRole"
      />
      <label class="form-check-label ms-2" :for="'role-' + item.id">
        {{ item.role }}
      </label>
    </div>
  </div>

  <p v-else class="text-muted italic">
    Please select a department to view available roles.
  </p>

  <p class="mt-3 text-success" v-if="selectedRole">
    Selected Destination Role: <strong>{{ selectedRole }}</strong>
  </p>

  <div
    class="card mt-4 mx-auto w-50 p-3 shadow-sm"
    v-if="selectedRole && currentSelectedEmployee"
  >
    <div class="card-header bg-primary text-white font-weight-bold">
      Automated Payroll Breakdown
    </div>
    <div class="card-body">
      <p class="d-flex justify-content-between">
        <span><strong>Gross Base Salary:</strong></span>
        <span>R{{ currentSelectedEmployee.baseSalary }}.00</span>
      </p>
      <p class="d-flex justify-content-between text-danger">
        <span><strong>Estimated Deductions (20% Tax):</strong></span>
        <span>-R{{ calculateTax }}.00</span>
      </p>
      <hr />
      <h5 class="d-flex justify-content-between text-success font-weight-bold">
        <span>Take-Home Net Pay:</span>
        <span>R{{ calculateNetPay }}.00</span>
      </h5>
    </div>
  </div>
</div>
</div>
</template>

<script>
export default {
  name: "Payroll",
  props: {
    uploadPayroll: String,
  },

  data() {
    return {
      selectedDepartment: "",// created empty objects to store our inputed information 
      selectedRole: "",
      rolesApiData: [  //Declared our Database to use for our payslip/payroll calculatinos 
        {
          id: 1,
          name: "Alice Johnson",
          department: "Development",
          role: "Software Engineer",
          empNum: "MTS001",
          tenure: "3 Years",
          baseSalary: 7500,
        },
        {
          id: 2,
          name: "Bob Smith",
          department: "Design",
          role: "UI/UX Designer",
          empNum: "MTS002",
          tenure: "2 Years",
          baseSalary: 6200,
        },
        {
          id: 3,
          name: "Charlie Brown",
          department: "Marketing",
          role: "SEO Specialist",
          empNum: "MTS003",
          tenure: "4 Years",
          baseSalary: 5100,
        },
        {
          id: 4,
          name: "David Miller",
          department: "Development",
          role: "Frontend Developer",
          empNum: "MTS004",
          tenure: "1 Year",
          baseSalary: 5800,
        },
        {
          id: 5,
          name: "Elena Rostova",
          department: "HR",
          role: "HR Generalist",
          empNum: "MTS005",
          tenure: "5 Years",
          baseSalary: 5400,
        },
        {
          id: 6,
          name: "Franklin Chang",
          department: "Finance",
          role: "Financial Analyst",
          empNum: "MTS006",
          tenure: "3 Years",
          baseSalary: 6800,
        },
        {
          id: 7,
          name: "Grace Hopper",
          department: "Development",
          role: "Backend Engineer",
          empNum: "MTS007",
          tenure: "6 Years",
          baseSalary: 8500,
        },
        {
          id: 8,
          name: "Henry Cavill",
          department: "Support",
          role: "IT Support Specialist",
          empNum: "MTS008",
          tenure: "8 Months",
          baseSalary: 4200,
        },
        {
          id: 9,
          name: "Ivy Green",
          department: "Design",
          role: "Graphic Designer",
          empNum: "MTS009",
          tenure: "2 Years",
          baseSalary: 4800,
        },
        {
          id: 10,
          name: "Jack Ryan",
          department: "Security",
          role: "Cybersecurity Analyst",
          empNum: "MTS010",
          tenure: "4 Years",
          baseSalary: 7200,
        },
        {
          id: 11,
          name: "Karen Martinez",
          department: "Marketing",
          role: "Content Strategist",
          empNum: "MTS011",
          tenure: "1.5 Years",
          baseSalary: 4900,
        },
        {
          id: 12,
          name: "Leo Dasilva",
          department: "Product",
          role: "Product Manager",
          empNum: "MTS012",
          tenure: "3 Years",
          baseSalary: 7800,
        },
        {
          id: 13,
          name: "Mia Wong",
          department: "Finance",
          role: "Accountant",
          empNum: "MTS013",
          tenure: "2.5 Years",
          baseSalary: 6100,
        },
        {
          id: 14,
          name: "Nathan Drake",
          department: "Support",
          role: "Customer Success Lead",
          empNum: "MTS014",
          tenure: "5 Years",
          baseSalary: 5500,
        },
        {
          id: 15,
          name: "Olivia Vance",
          department: "HR",
          role: "Talent Acquisition",
          empNum: "MTS015",
          tenure: "1 Year",
          baseSalary: 5300,
        },
      ],
    };
  },

  mounted() {
    this.loadLocalEmployees(); // mounted to pull all our local employee data 
  },
  methods: {
    loadLocalEmployees() {
      console.log(
        "Local employee records loaded successfully!",
        this.rolesApiData.length,
      );
    },
  },
  computed: {
    // 1. department filter 
    filteredRoles() {
      if (!this.selectedDepartment || !this.rolesApiData) return [];
      return this.rolesApiData.filter(
        (item) => item && item.department === this.selectedDepartment,
      );
    },

    // Check employee that has been seleceted and choose role 
    currentSelectedEmployee() {
      if (!this.selectedRole) return null;
      // Find the record matching the role selected via the radio button
      return this.rolesApiData.find((emp) => emp.role === this.selectedRole);
    },

    // Automated Tax Calculation (Simulating a flat 20% tax rate)
    calculateTax() {
      const employee = this.currentSelectedEmployee;
      if (!employee) return 0;

      return employee.baseSalary * 0.2; // 20% Tax
    },

    // Automated Net Pay Calculation (Base Salary minus Tax)
    calculateNetPay() {
      const employee = this.currentSelectedEmployee;
      if (!employee) return 0;

      return employee.baseSalary - this.calculateTax;
    },
  },
};
</script>

<style scoped>
</style>
