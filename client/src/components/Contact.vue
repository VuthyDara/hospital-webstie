<template>
  <div class="contact">
    <h3>Contact Us</h3><hr>
      <div class="emergency">
    <div class="left">
      <h4 id="greet">THANK YOU FOR CONTACTING US!<br>
      Get In Touch</h4><br>
      <span>Tel: +855 12 345 678</span><br>
      <span>&emsp;&ensp; +855 12 345 678</span>
    </div>
    
  </div>
    <div class="box">
      <h4>Thank you for contacting Our Hospital.
Please use this form for inquiries about our services or for sharing your feedback.</h4>
      <div class="row">
        <div>
          <form action="#">
            <div class="custom-input" id="patient-name">
              <img src="../assets/patient.png">
              <input 
                v-model="form.name" 
                id="message" rows="3" 
                @input="validateContent"
                placeholder="Full Name">
            </div>
          </form>
        </div>
      </div>
      <div class="row">
        <div>
            <form action="#">
              <div class="custom-input">
                <img src="../assets/phonenumber.png">
                <input 
                  v-model="form.tel"
                  id="tel" rows="2" 
                  @input="validateContent"
                  placeholder="Phone Number">
              </div>
            </form>
          </div>   
          <div>
            <form action="#">
              <div class="custom-input">
                <img src="../assets/email.png">
                <input
                  v-model="form.email"
                  id="email" rows="2" 
                  @input="validateContent" 
                  placeholder="Email Address">
              </div>
            </form>
          </div>
         </div>
         <div class="row">
          <div>
            <form action="#">
              <div class="custom-input" id="contact-input">
                <img src="../assets/text.png" class="img">
                <input 
                  v-model="form.message" 
                  id="name" rows="1" 
                  @input="validateContent"
                  placeholder="Message...">
              </div>
            </form>
          </div>
        </div>
        <div class="last">
         <h5>Thanks you for contacting with Our Hospital!<br>
Our customer service will contact you back soon..</h5>
        <button class="button" @click="submitContact" type="submit">Submit Request</button>
        </div>
     </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import axios from 'axios'
export default {
  name: 'Contact',
  data() {
    return {
      form: {
        message: '',
        name: '',
        tel: '',
        email: '',
      },
      error: {}
    }
  },
  props: {
    msg: String
  },
  methods: {
    validateContent() {
      if (this.form.message && this.form.name && this.form.tel && this.form.email != "") {
        this.error.message = null
      }
    },
    submitContact() {
      // Validation content
      if (this.form.message && this.form.name && this.form.tel && this.form.email == "") {
        this.error.message = "Everything should be filled"
      }
      // Post content to server
      axios.post('http://localhost:4000/contacts', this.form)
        .then(function (response) {
          console.log(response);
        })
        .catch(function (error) {
          console.log(error);
        });
    }
  },
  computed: {
    hasError() {
      if(this.error.message) return true
      return false
    },
    ...mapGetters([
      "getContacts"
    ]), // mapGetters() will return ["getPosts"] => "getPosts"
  }
}
</script>

<style scoped>
.contact {
  width: 100%;
}
.button {
  border: 1px solid #999797 ;
  border-radius: 1em;
  height: 2em;
  margin-top: 1em;
}
.left {
  font-size: 1.5em;
  text-align: left;
}
span {
  font-size: 0.75em;
  padding: 0em 0em 2em 3em;
  margin-top: -5em;
}
#greet {
  padding: 2em 2em 0em 2em;
  margin-bottom: 0em;
}
#patient-name {
  width: 43em;
  margin-left: 2em;
  margin-right: 2em;
}
h3 {
    text-align: left;
    font-size: 1.5em;
}
h5 {
  text-align: left;
}
hr {
    margin-top: -0.5em;
}

h4 {
  font-size: 1em;
  padding: 1.5em 4em 1.5em 4em;
}
.last {
  display: flex;
  justify-content: space-between;
  padding: 2em 4em 2em 4em;
}
#national {
  width: 20px;
  height: 20px;
}
.box {
  width: 70%;
  margin: auto;
  display: block;
  border: 1px solid #e6e4e4;
  background-color: white;
}

a {
  color: black;
}

.row {
  display: flex;
  justify-content: center;
  margin-top: 10px;
}

#contact-input {
  width: 43em;
  height: 10em;
  margin-left: 2em;
  margin-right: 2em;
}
.custom-input {
  background-color: white;
  border: 2px solid #ededed;
  margin-left: 1.5em;
  margin-right: 1.5em;
  padding: 5px;
  width:20em;
  border-radius: 5px;
  text-align: start;
}

.custom-input>* {
  vertical-align: middle;
  width: 90%;
}

.custom-input img {
  width: 14px;
  height: 14px;
  display: inline-block;
}

.custom-input input {
  border: none;
  height: 18px;
  display: inline-block;
  outline: none;
  margin-left: 0.5em;
}


input {
  width: 80%;
  font-size: 0.8em;
}

.emergency {
  height: 18em;
  margin-top: 3em;
  background-color: #bd1122;
  color: white;
  margin-bottom: -1.5em;
}





</style>