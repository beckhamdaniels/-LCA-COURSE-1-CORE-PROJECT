<template>
  <div class="container py-4">
    <h1 class="mb-4 text-center">{{ title }}</h1>

    <div class="card-group">
      <div v-for="employee in rolesApiData" :key="employee.id" class="card mb-3 shadow-sm" >
        <img 
          src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSzCj4TUt2nYcMXBv_lgwk_iS8wCKWGwZChLLCsWQ5EUvT8Gee_dIbhwdaB&s=10" 
          class="card-img-top img-fluid" 
          alt="Placeholder"
        />
        <div class="card-body">
          <h5 class="card-title">Name: {{ employee.name }}</h5>
          <p class="card-text">Department: {{ employee.department }}</p>
          <p class="card-text">Role: {{ employee.role }}</p>
          <p class="card-text">Employee Number: {{ employee.empNum }}</p>
          <p class="card-text"><small class="text-muted">Tenure: {{ employee.tenure }}</small></p>
        </div>
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'EmployeeDirectory',
  props: {
    title: String,
  },
  data() { //declared the Database for our Employee Directory 
    return {
      rolesApiData: [
        { id: 1, name: "Alice Johnson", department: "Development", role: "Software Engineer", empNum: "MTS001", tenure: "3 Years", baseSalary: 7500 },
        { id: 2, name: "Bob Smith", department: "Design", role: "UI/UX Designer", empNum: "MTS002", tenure: "2 Years", baseSalary: 6200 },
        { id: 3, name: "Charlie Brown", department: "Marketing", role: "SEO Specialist", empNum: "MTS003", tenure: "4 Years", baseSalary: 5100 },
        { id: 4, name: "David Miller", department: "Development", role: "Frontend Developer", empNum: "MTS004", tenure: "1 Year", baseSalary: 5800 },
        { id: 5, name: "Elena Rostova", department: "HR", role: "HR Generalist", empNum: "MTS005", tenure: "5 Years", baseSalary: 5400 },
        { id: 6, name: "Franklin Chang", department: "Finance", role: "Financial Analyst", empNum: "MTS006", tenure: "3 Years", baseSalary: 6800 },
        { id: 7, name: "Grace Hopper", department: "Development", role: "Backend Engineer", empNum: "MTS007", tenure: "6 Years", baseSalary: 8500 },
        { id: 8, name: "Henry Cavill", department: "Support", role: "IT Support Specialist", empNum: "MTS008", tenure: "8 Months", baseSalary: 4200 },
        { id: 9, name: "Ivy Green", department: "Design", role: "Graphic Designer", empNum: "MTS009", tenure: "2 Years", baseSalary: 4800 },
        { id: 10, name: "Jack Ryan", department: "Security", role: "Cybersecurity Analyst", empNum: "MTS010", tenure: "4 Years", baseSalary: 7200 },
        { id: 11, name: "Karen Martinez", department: "Marketing", role: "Content Strategist", empNum: "MTS011", tenure: "1.5 Years", baseSalary: 4900 },
        { id: 12, name: "Leo Dasilva", department: "Product", role: "Product Manager", empNum: "MTS012", tenure: "3 Years", baseSalary: 7800 },
        { id: 13, name: "Mia Wong", department: "Finance", role: "Accountant", empNum: "MTS013", tenure: "2.5 Years", baseSalary: 6100 },
        { id: 14, name: "Nathan Drake", department: "Support", role: "Customer Success Lead", empNum: "MTS014", tenure: "5 Years", baseSalary: 5500 },
        { id: 15, name: "Olivia Vance", department: "HR", role: "Talent Acquisition", empNum: "MTS015", tenure: "1 Year", baseSalary: 5300 }
      ]
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card-group{
  display:grid;
  grid-template-columns: repeat(5, 1fr);
  gap :15px;
  padding-bottom:20px;
}

.card{
  max-width: 350px;
  border: 2px solid black;
  border-left : 2px solid black !important;
  border-radius: 5px !important;
  margin : 0 auto;
  visibility: visible;

}
</style>
