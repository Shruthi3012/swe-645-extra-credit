<template>
  <div class="container mt-4">
    <div class="row">
      <div class="col-sm-1"></div>
      <div class="col-sm-10 shadow p-3 mb-5 bg-body rounded">
        <h2 class="text-center">View Survey Details</h2>
        <hr />
        <div>
          <!-- Display survey details -->
          <p><strong>First Name:</strong> {{ survey.firstName }}</p>
          <p><strong>Last Name:</strong> {{ survey.lastName }}</p>
          <p><strong>Street Address:</strong> {{ survey.streetAddress }}</p>
          <p><strong>City:</strong> {{ survey.city }}</p>
          <p><strong>State:</strong> {{ survey.state }}</p>
          <p><strong>Zip:</strong> {{ survey.zip }}</p>
          <p><strong>Telephone Number:</strong> {{ survey.telephoneNumber }}</p>
          <p><strong>E-mail:</strong> {{ survey.email }}</p>
          <p><strong>Survey Date:</strong> {{ survey.date }}</p>
          
          <!-- Handle array fields like selectedCampusLikes -->
          <p><strong>What do you like most about the campus?</strong> 
            <!-- Display the likes from the array if present -->
            <span v-if="survey.selectedCampusLikes && survey.selectedCampusLikes.length">
              {{ survey.selectedCampusLikes.join(', ') }}
            </span>
          </p>
          <p><strong>How did you become interested in the University?</strong> {{ survey.universityInterest }}</p>
          <p><strong>How much would you recommend this university?</strong> {{ survey.recommendUniversity }}</p>
          <p><strong>Raffle:</strong> {{ survey.raffle }}</p>
          <p><strong>Comments:</strong> {{ survey.comments }}</p>
        </div>
        
        <div class="text-center mt-4">
          <!-- Back Button styled to match Save Changes button -->
          <button class="btn btn-success" @click="goBack">Back</button>
        </div>
      </div>
      <div class="col-sm-1"></div>
    </div>
  </div>

  <!-- Footer -->
  <footer class="footer mt-auto py-3">
    <div class="container">
      <div class="row text-center">
        <div class="col-12">
          <span class="text-white">Copyright &copy; 2024 Shruthi Pachava | </span>
          <span class="text-white">spachava@gmu.edu </span>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'ViewSurvey',
  data() {
    return {
      survey: this.$route.params.survey || {} 
    };
  },
  methods: {
    goBack() {
      this.$router.push('/'); 
    }
  }
};
</script>

<style scoped>
/* Styles for Footer */
.footer {
  background-color: #006633;
  color: white;
  width: 100%;
}
</style>
