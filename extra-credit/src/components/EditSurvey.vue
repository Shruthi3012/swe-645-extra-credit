<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-2"></div>
      <div class="col-sm-8 shadow p-3 mb-5 bg-body rounded">
        <form @submit.prevent="submitSurvey">
          <h2 class="text-center">Edit Survey</h2>
          <hr />

          <!-- Input Fields -->
          <div class="form-group text-start">
            <label for="firstName">First Name<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="survey.firstName" placeholder="Enter first name" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="lastName">Last Name<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="survey.lastName" placeholder="Enter last name" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="streetAddress">Street Address<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="survey.streetAddress" placeholder="Enter street address" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="city">City<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="survey.city" placeholder="Enter city" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="state">State<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="survey.state" placeholder="Enter state" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="zip">Zip<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="survey.zip" placeholder="Enter zip" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="telephoneNumber">Telephone Number<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="survey.telephoneNumber" placeholder="Enter telephone number" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="email">E-mail<span class="text-danger">*</span></label>
            <input type="email" class="form-control" v-model="survey.email" placeholder="Enter email" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="date">Survey Date<span class="text-danger">*</span></label>
            <input type="date" class="form-control" v-model="survey.date" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label>What do you like most about the campus?</label>
            <div class="form-check" v-for="(option, index) in campusLikes" :key="index">
              <input class="form-check-input" type="checkbox" v-model="survey.selectedCampusLikes" :value="option" />
              <label class="form-check-label">{{ option }}</label>
            </div>
          </div>
          <br />
          <div class="form-group text-start">
            <label>How did you become interested in the University?</label>
            <div class="form-check" v-for="(option, index) in universityInterestOptions" :key="index">
              <input class="form-check-input" type="radio" v-model="survey.universityInterest" :value="option" />
              <label class="form-check-label">{{ option }}</label>
            </div>
          </div>
          <br />
          <div class="form-group text-start">
            <label for="recommendUniversity">How much would you recommend this university?</label>
            <select class="form-select" v-model="survey.recommendUniversity">
              <option value="" disabled>Select an option</option>
              <option value="1">Very Likely</option>
              <option value="2">Likely</option>
              <option value="3">Unlikely</option>
            </select>
          </div>
          <br />
          <div class="form-group text-start">
            <label for="raffle">Raffle - Enter at least ten comma-separated numbers ranging from 1 through 100</label>
            <input type="text" class="form-control" v-model="survey.raffle" placeholder="Enter at least ten comma-separated numbers" />
          </div>
          <br />
          <div class="form-group text-start">
            <label>Comments</label>
            <textarea class="form-control" v-model="survey.comments" rows="3"></textarea>
          </div>
          <br />

          <!-- Submit and Cancel Buttons -->
          <div class="row text-center">
            <div class="col-12">
              <button type="button" class="btn btn-success mx-2" @click="cancelEdit">Cancel</button>
              <button type="submit" class="btn btn-success mx-2">Save Changes</button>
            </div>
          </div>
        </form>
      </div>
      <div class="col-sm-2"></div>
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
  name: 'EditSurvey',
  data() {
    return {
      survey: this.$route.params.survey || {}, // Assuming survey data is passed via route params
      campusLikes: [
        'Students',
        'Location',
        'Campus',
        'Atmosphere',
        'Dorm rooms',
        'Sports'
      ],
      universityInterestOptions: ['Friends', 'Television', 'Internet', 'Other']
    };
  },
  methods: {
    submitSurvey() {
      console.log('Updated survey:', this.survey);
      this.$router.push('/'); 
    },
    cancelEdit() {
      this.$router.push('/'); 
    }
  }
};
</script>

<style scoped>
.footer {
  background-color: #006633;
  width: 100%;
  bottom: 0;
}
</style>
