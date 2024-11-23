<template>
  <div class="container mt-4">
    <div class="row">
      <div class="col-sm-1"></div>
      <div class="col-sm-10 shadow p-3 mb-5 bg-body rounded">
        <div class="mb-3 text-center position-relative">
          <h2 class="text-center">Survey Management</h2>
          <hr />
          <button class="btn btn-success position-absolute end-0" @click="addSurvey">Add Survey</button>
          <br /><br />
        </div>
        <table class="table table-bordered table-striped">
          <thead class="custom-header">
            <tr>
              <th>#</th>
              <th>Survey Name</th>
              <th>Created Date</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(survey, index) in surveys" :key="index">
              <td>{{ index + 1 }}</td>
              <td>{{ survey.name }}</td>
              <td>{{ survey.date }}</td>
              <td class="text-center">
                <div class="action-buttons">
                  <button class="btn btn-sm btn-success" @click="viewSurvey(index)">View</button>
                  <button class="btn btn-sm btn-success" @click="editSurvey(index)">Edit</button>
                  <button class="btn btn-sm btn-success" @click="deleteSurvey(index)">Delete</button>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="col-sm-1"></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      surveys: [
        { name: "Student Feedback", date: "2024-11-23" },
        { name: "Event Survey", date: "2024-11-22" },
      ],
    };
  },
  methods: {
    addSurvey() {
      this.$router.push('/survey');  // Add this line to navigate to survey page
    },
    viewSurvey(index) {
      alert(`Viewing survey: ${this.surveys[index].name}`);
    },
    editSurvey(index) {
      alert(`Editing survey: ${this.surveys[index].name}`);
    },
    deleteSurvey(index) {
      if (confirm(`Are you sure you want to delete ${this.surveys[index].name}?`)) {
        this.surveys.splice(index, 1);
      }
    },
  },
};
</script>

<style scoped>
.footer {
  background-color: #006633;
  width: 100%;
  bottom: 0;
}
.custom-header {
  background-color: #006633;
  color: white;
}
.action-buttons {
  display: flex;
  justify-content: center;
  gap: 0.5rem; /* Adds space between buttons */
}
</style>