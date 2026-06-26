<template>
  <h1>ModernTech Solutions</h1> 

  <nav class="navbar navbar-expand-lg bg-body-tertiary"> 
    <div class="container-fluid">
      <a class="navbar-brand" href="#">
        <img
          src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQlekMn0kLJTMwXYu6n-Dq-YetNYgXEKP077EsdpBPbnQ&s=10"
          alt="MTS"
          width="100px"
        />
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNavDropdown"
        aria-controls="navbarNavDropdown"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavDropdown">
        <ul class="navbar-nav">
          <li class="nav-item">
            <a
              class="nav-link"
              :class="{ active: activePage === 'home' }" 
              href="#"
              @click.prevent="activePage = 'home'"
              >Home</a
            >
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              :class="{ active: activePage === 'employee-directory' }"
              href="#"
              @click.prevent="activePage = 'employee-directory'"
              >Employee Directory</a
            >
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              :class="{ active: activePage === 'apply-leave' }"
              href="#"
              @click.prevent="activePage = 'apply-leave'"
              >Apply Leave</a
            >
          </li>
          <li class="nav-item dropdown">
            <a
              class="nav-link dropdown-toggle"
              href="#"
              role="button"
              data-bs-toggle="dropdown"
              aria-expanded="false"
            >
              More
            </a>
            <ul class="dropdown-menu">
              <li>
                <a
                  class="dropdown-item"
                  :class="{ active: activePage === 'payroll' }"
                  href="#"
                  @click.prevent="activePage = 'payroll'"
                  >Generate Payslip</a
                >
              </li>
              <li>
                <a
                  class="dropdown-item"
                  :class="{ active: activePage === 'generate-payslip' }"
                  href="#"
                  @click.prevent="activePage = 'generate-payslip'"
                  >Payroll</a
                >
              </li>
              <li><a class="dropdown-item" :class="{ active: activePage === 'attendance' }"
                  href="#"
                  @click.prevent="activePage = 'attendance'">Attendance</a></li>
            </ul>
          </li>
        </ul>
      </div>
    </div>
    <form class="d-flex justify-content-end" role="search">
      <input
        class="form-control me-2"
        id="search"
        type="search"
        placeholder="Search"
        aria-label="Search"
        v-model="searchWeb"
      />
      <button class="btn btn-outline-success" type="submit">Search</button>
    </form>
  </nav>

  <div v-if="activePage === 'home'"> 
    <HelloWorld msg="Meet the Department Heads" />
  </div>

  <div v-else-if="activePage === 'employee-directory'">
    <EmployeeDirectory title="Employee Directory" />
  </div>

  <div v-else-if="activePage === 'apply-leave'">
    <ApplyLeave leave="Apply Leave" />
  </div>

  <div v-else-if="activePage === 'generate-payslip'">
    <GeneratePayslip payslip="Upload Variable Payroll" />
  </div>

  <div v-else-if="activePage === 'payroll'">
    <Payroll uploadPayroll="Generate Payslip" />
  </div>

  <div v-else-if="activePage === 'attendance'">
    <ViewAttendance view="View Attendance" />
  </div>

  <footer>
    <div class="pageEnd">
      <p>ModernTech Solutions ©️</p>
      <p>EST 2010</p>
      <div class="contactDets">
        <p>📞 : +27 71 234 5678</p>
        <p>✉️ : mytechsolutionssa@gmail.co.za</p>
        <p>🌐 : http://localhost:8080/#</p>
      </div>
    </div>
  </footer>
</template>

<script>
import EmployeeDirectory from "./components/EmployeeDirectory.vue";  //Importing each tab to the main screen 
import HelloWorld from "./components/HelloWorld.vue";
import ApplyLeave from "./components/ApplyLeave.vue";
import GeneratePayslip from "./components/GeneratePayslip.vue";
import Payroll from "./components/Payroll.vue";
import ViewAttendance from "./components/Attendance.vue";

export default {
  name: "App",
  //crated components for each screen
  components: {
    HelloWorld,
    EmployeeDirectory,
    ApplyLeave,
    GeneratePayslip,
    Payroll,
    ViewAttendance
  },
  data() {
    return {
      activePage: "home", // declared this page as the 'home' page to start the switch
      searchWeb: "",
    };
  },
};
</script>

<style>
template {
  background-color: #f4f6f8;
}

h1 {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.card {
  align-items: center;
}

.pageEnd {
  padding-top: 10px;
  background-color: #1f3a5f;
  color: white;
}

.contactDets {
  border: 1px solid grey;
  border-radius: 20px;
  align-items: center;
  width: fit-content;
  margin: 0 auto;
  padding: 50px 50px;
}


html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  overflow-x: hidden; 
}


h1 {
  font-size: 2.5rem;
}

/* --- TABLET VIEWPORT ADJUSTMENTS --- */
@media (max-width: 992px) {
  h1 {
    font-size: 2rem; 
  }
  
  
  .card-group {
    grid-template-columns: repeat(3, 1fr) !important;
  }
  
  .contactDets {
    padding: 30px 20px !important;
    width: 90% !important;
  }
}

/* --- SMARTPHONE VIEWPORT ADJUSTMENTS --- */
@media (max-width: 576px) {
  h1 {
    font-size: 1.6rem;
    text-center: true;
  }
  

  .card-group {
    grid-template-columns: 1fr !important;
    padding: 10px;
  }
  

  .w-25, .w-50, .w-75 {
    width: 100% !important;
  }
  
  
  .contactDets {
    padding: 20px 10px !important;
    border-radius: 10px !important;
  }
  
  
  .sticky-image-container {
    position: static !important; 
    width: 100%;
  }
}
</style>
