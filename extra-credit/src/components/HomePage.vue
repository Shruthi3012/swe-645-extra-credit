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
                  <!-- View Survey Button -->
                  <router-link :to="`/survey/${index}/view`" class="btn btn-sm btn-success">View</router-link>
                  <!-- Edit Survey Button -->
                  <router-link :to="`/survey/${index}/edit`" class="btn btn-sm btn-success">Edit</router-link>
                  <!-- Delete Survey Button -->
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
      this.$router.push('/survey'); // Navigate to Add Survey page
    },
    // View Survey method: Routes to the survey view page
    viewSurvey(index) {
      this.$router.push(`/survey/${index}/view`); // Navigate to View Survey page
    },
    // Edit Survey method: Routes to the survey edit page
    editSurvey(index) {
      this.$router.push(`/survey/${index}/edit`); // Navigate to Edit Survey page
    },
    // Delete Survey method: Removes survey from the list
    deleteSurvey(index) {
      if (confirm(`Are you sure you want to delete ${this.surveys[index].name}?`)) {
        this.surveys.splice(index, 1); // Remove survey from the list
      }
    },
  },
};
</script>

<style scoped>
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
