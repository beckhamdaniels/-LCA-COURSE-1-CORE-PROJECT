<template>
  <div class="container-fluid py-4">
    <h1>{{ msg }}</h1>
    <div class="row">
      
      <div class="col-md-6 d-flex flex-column align-items-center">
        <div  v-for="employee in rolesApiData" :key="employee.id" class="card mb-3" style="max-width: 540px">
          <div class="row g-0">
            <div class="col-md-4">
              <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSzCj4TUt2nYcMXBv_lgwk_iS8wCKWGwZChLLCsWQ5EUvT8Gee_dIbhwdaB&s=10" class="img-fluid rounded-start" alt="PlaceHolder" />
            </div>
            <div class="col-md-8">
              <div class="card-body">
                <h5 class="card-title">Name : {{employee.name}}</h5>
                <p class="card-text">Department: {{employee.department}}</p>
                <p class="card-text"><small class="text-body-secondary">Quote: {{employee.quote}}</small></p>
              </div>
            </div>
          </div>
        </div>
      </div>



      <div class="col-md-6 d-flex justify-content-center align-items-start pt-2">
        <div class="sticky-image-container">
          <div class="mb-4 text-center">
            <img src="https://capetownoffice.com/wp-content/uploads/2019/08/IMG_20190513_073428.jpg" class="rounded img-fluid" alt="Office" style="max-width: 540px" />
            <p class="text-muted mt-2">One of Our Cape Town Office Spaces</p>
          </div>

          <div class="mb-4 text-center">
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSqxH9Npon4Em_yEc4TZpJPcWMZ92wB3zCoMWCPmFncF5cbOAxDaKL4_Aq2&s=10" class="rounded img-fluid" alt="Scenery" style="max-width: 540px" />
            <p class="text-muted mt-2">Our Joburg Office</p>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data(){    // declared the database for the four Leads
    return{
     rolesApiData: [
        {
          id: 1,
          name: "Liyema Nkosi",
          department: "Software Development",
          quote: "Coding is just like taking a MyCiTi bus—as long as your routes are correctly mapped, you'll reach your destination.",
        
        },
        {
          id: 2,
          name: "Ayesha Patel",
          department: "UI/UX Design",
          quote: "Design is not just what it looks like. It's about making sure the user can find the 'Buy' button before their data bundles run out!",
        },
        {
          id: 3,
          name: "Sipho Ndlovu",
          department: "Customer Success",
          quote: "Treating every client like they are ordering the first hot koesister on a Sunday morning—with warmth and premium care.",
        },
        {
         id: 4,
          name: "Thando Molefe",
          department: "Talent Acquisition",
          quote: "We aren't just looking for skills in Cape Town; we are looking for that local gees that brings a development team to life.",
        }
      ]
    }
  },
}
</script>

<style scoped>
.card {
  display: flex;
  justify-content: center;
}

.sticky-image-container {
  position: sticky;
  top: 20px;
  max-width: 540px;
  width: 100%;
}
</style>