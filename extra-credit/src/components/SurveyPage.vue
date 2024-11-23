<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-2"></div>
      <div class="col-sm-8 shadow p-3 mb-5 bg-body rounded">
        <form>
          <br />
          <h2 class="text-center">Student Survey Form</h2>
          <hr />
          <div class="form-group text-start">
            <label for="firstName">First Name<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="firstName" placeholder="Enter first name" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="lastName">Last Name<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="lastName" placeholder="Enter last name" required />
          </div>
          <br />
          <div class="form-group text-start" >
            <label for="streetAddress">Street Address<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="streetAddress" placeholder="Enter street address" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="city">City<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="city" placeholder="Enter city" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="state">State<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="state" placeholder="Enter state" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="zip">Zip<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="zip" placeholder="Enter zipcode" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="telephoneNumber">Telephone Number<span class="text-danger">*</span></label>
            <input type="text" class="form-control" v-model="telephoneNumber" placeholder="Enter telephone number" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="email">E-mail<span class="text-danger">*</span></label>
            <input type="email" class="form-control" v-model="email" placeholder="Enter email" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label for="date">Survey Date<span class="text-danger">*</span></label>
            <input type="date" class="form-control" v-model="date" placeholder="Select a date" required />
          </div>
          <br />
          <div class="form-group text-start">
            <label>What do you like most about the campus?</label>
            <div class="form-check" v-for="(option, index) in campusLikes" :key="index">
              <input class="form-check-input" type="checkbox" v-model="selectedCampusLikes" :value="option" />
              <label class="form-check-label">{{ option }}</label>
            </div>
          </div>
          <br />
          <div class="form-group text-start">
            <label>How did you become interested in the University?</label>
            <div class="form-check" v-for="(option, index) in universityInterestOptions" :key="index">
              <input class="form-check-input" type="radio" v-model="universityInterest" :value="option" />
              <label class="form-check-label">{{ option }}</label>
            </div>
          </div>
          <br />
          <div class="form-group text-start">
            <label>How much would you like to recommend this university?</label>
            <select class="form-select" v-model="recommendUniversity">
              <option value="" disabled selected>Select an option</option>
              <option value="1">Very Likely</option>
              <option value="2">Likely</option>
              <option value="3">Unlikely</option>
            </select>
          </div>
          <br />
          <div class="form-group text-start">
            <label for="raffle">Raffle - Enter at least ten comma-separated numbers ranging from 1 through 100</label>
            <input type="text" class="form-control" v-model="raffle" placeholder="enter at least ten comma-separated numbers" />
          </div>
          <br />
          <div class="form-group text-start">
            <label>Comments</label>
            <textarea class="form-control" v-model="comments" rows="3"></textarea>
          </div>
          <br />
          <div class="row text-center">
            <div class="col-12">
              <button type="button" class="btn btn-success mx-2" @click="cancelForm">Cancel</button>
              <button type="submit" class="btn btn-success mx-2">Submit</button>
            </div>
          </div>
        </form>
      </div>
      <div class="col-sm-2"></div>
    </div>
  </div>
  <footer class="footer mt-auto py-3">
    <div class="container">
      <div class="row text-center">
        <div class="col-12">
          <span class="text-white">Copyright &copy;</span>
          <span class="text-white">2024 Shruthi Pachava | </span>
          <span class="text-white">spachava@gmu.edu </span>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
   name: 'SurveyPage',
  data() {
    return {
      firstName: "",
      lastName: "",
      streetAddress: "",
      city: "",
      state: "",
      zip: "",
      telephoneNumber: "",
      email: "",
      date: "",
      selectedCampusLikes: [],
      universityInterest: "",
      recommendUniversity: "",
      raffle: "",
      comments: "",
      campusLikes: [
        "Students",
        "Location",
        "Campus",
        "Atmosphere",
        "Dorm rooms",
        "Sports"
      ],
      universityInterestOptions: ["Friends", "Television", "Internet", "Other"]
    };
  },
  methods: {
    cancelForm() {
      // Logic to reset the form or handle cancellation
      this.$router.push("/");
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
