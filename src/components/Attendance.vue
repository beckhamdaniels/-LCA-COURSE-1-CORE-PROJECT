<template>
  <div class="container py-4">
    <h1 class="mb-4 text-center">Attendance & Leave Management</h1>
    
    <div class="card shadow-sm w-75 mx-auto">
      <div class="card-header bg-dark text-white font-weight-bold text-start">
        Pending Leave Requests (HR Action Required)
      </div>
      <div class="card-body">
        <div class="table">
          <table class="table align-middle">
            <thead class="table-light">
              <tr>
                <th>Emp ID</th>
                <th>Employee Name</th>
                <th>Leave Type</th>
                <th>Duration</th>
                <th>Status</th>
                <th>Actions</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="request in mockRequests" :key="request.id">
                <td>{{ request.empId }}</td>
                <td><strong>{{ request.name }}</strong></td>
                <td>{{ request.type }}</td>
                <td>{{ request.dates }}</td>
                <td> 
                    {{ request.status }}
                </td>
                <td>
                  <div v-if="request.status === 'Pending'" class="btn-group btn-group-sm">
                    <button class="btn btn-success">Approve</button>
                    <button  class="btn btn-danger">Deny</button>
                  </div>
                  <span v-else class="text-muted italic small">Processed</span>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ViewAttendance",
  data() {
    return {
      mockRequests: [  // mock leace requests 
        { id: 1, empId: "MTS002", name: "Bob Smith", type: "Annual Leave", dates: "12 Jul - 15 Jul", status: "Pending" },
        { id: 2, empId: "MTS005", name: "Elena Rostova", type: "Paid Sick Leave", dates: "01 Aug - 03 Aug", status: "Pending" },
        { id: 3, empId: "MTS008", name: "Henry Cavill", type: "Emergency Leave", dates: "28 Jun - 29 Jun", status: "Approved" }
      ]
    };
  },
};
</script>

<style scoped>

.table-bordered {
  border: 1px solid #dee2e6;
}
</style>