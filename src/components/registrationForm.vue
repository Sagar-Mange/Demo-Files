<template>
<div>
<div :style="myStyle">
  <form v-if="!submitted" id="validated-form">
        <div class="temp">
        <h1 style="padding-top:2%">REGISTRATION FORM</h1>
        <hr><br>
        <label for="name" class="label">Your Name</label>
        <input class="input" type="text" id="name" v-model.trim="user.name">
        <p class="error" v-if="!nameIsValid">* Name Field is Invalid</p>
        </div>

        <div class="temp">
        <label for="email" class="label">Your Email</label>
        <input class="input" type="email" id="email" v-model.trim="user.email">
        <p class="error" v-if="!emailIsValid">* Email Field is Invalid</p>
        </div>

        <div class="temp">
        <label for="mobile" class="label">Mobile No.</label>
        <input class="input" number v-model.trim="user.mobile" type="tel" id="mobile">
        <p class="error" v-if="!mobileIsValid">* Mobile No.is Invalid</p>
        </div>

        <div class="temp">
        <h2 style="padding-top:10px;font-size: 23px;font-family:sans-serif">Task Done</h2>

        <input type="checkbox" id="checkbox" value="Task 1" v-model="user.checkedNames">
        <label for="checkbox" id="hobby">Task 1</label>

        <input type="checkbox" id="checkbox" value="Task 2" v-model="user.checkedNames">
        <label for="checkbox" id="hobby">Task 2</label>

        <input type="checkbox" id="checkbox" value="Task 3" v-model="user.checkedNames">
        <label for="checkbox" id="hobby">Task 3</label>

        <input type="checkbox" id="checkbox" value="Task 4" v-model="user.checkedNames">
        <label for="checkbox" id="hobby">Task 4</label>

        <input type="checkbox" id="checkbox" value="Task 5" v-model="user.checkedNames">
        <label for="checkbox" id="hobby">Task 5</label>
        </div>

        <div class="temp">
        <h2 style="padding-top:10px;font-size: 23px;font-family:sans-serif">Gender</h2>
        <input type="radio" id="gender" value="Male" v-model="user.picked">
        <label style="padding-right: 1.2%; font-size:20px" for="one">Male</label>
        <input type="radio" id="gender" value="Female" v-model="user.picked">
        <label style="font-size:20px" for="two">Female</label>
        </div>

        <div class="temp">
        <label for="password" class="label">Password</label>
        <input class="input" type="password" id="password" v-model="user.password">
        <p class="error" v-if="!passwordIsValid">* Password Field is Invalid because minimum 7 characters required</p>
        </div>

        <div class="temp">
        <input id='submitted' value="Submit" type="submit" @click.prevent="submitForm"/>
        </div>
    </form>
    <div v-if="submitted">
        <h3 style="font-family:sans-serif"> Thanks For Submitting Your Details </h3>
    </div>
    <div style="display:none" id="preview">
        <h3 id=data>D E T A I L S</h3>
        <p class="preview"> <label class="label">Your Name:</label> {{user.name}}    </p>
        <p class="preview"> <label class="label">Your Email:</label> {{user.email}}   </p>
        <p class="preview"> <label class="label">Mobile No.:</label> {{user.mobile}}  </p>
        <p class="preview"> <label style="padding-right:5.2%" class="label">Hobby  :</label> {{user.checkedNames}}  </p>
        <p class="preview"> <label style="padding-right:4.8%" class="label">Gender  :</label> {{user.picked}}  </p>
        <p class="preview"> <label style="padding-right:3.0%" class="label">Password  :</label> {{user.password}}</p>
    </div>
    </div>
</div>
</template>

<script>
export default {
  data () {
    return {
      myStyle: {
        backgroundColor: '#EAECEE'
      },
      user: {
        name: '',
        email: '',
        mobile: '',
        password: '',
        checkedNames: [],
        picked: ''
      },
      submitted: false
    }
  },
  computed: {
    nameIsValid () {
      return !!this.user.name
    },
    emailIsValid () {
      var reg = /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/
      return reg.test(this.user.email)
    },
    mobileIsValid () {
      return this.user.mobile.length != null && this.user.mobile.length === 10
    },
    passwordIsValid () {
      return this.user.password.length > 6
    },
    formIsValid () {
      return this.nameIsValid && this.emailIsValid && this.mobileIsValid && this.passwordIsValid
    }
  },
  methods: {
    submitForm () {
      if (this.formIsValid) {
        document.getElementById('submitted').onclick = alert('Form Is Valid & Submitted')
        // console.log('Form Submitted', this.user)
        document.getElementById('preview').style.display = 'block'
      } else {
        document.getElementById('submitted').onclick = alert('Form Is Invalid')
        // console.log('Form Is Invalid')
      }
      this.submitted = true
      console.log('name :', this.user.name)
      console.log('email :', this.user.email)
      console.log('mobile :', this.user.mobile)
      console.log('password :', this.user.password)
      console.log('hobby :', this.user.checkedNames)
      console.log('gender :', this.user.picked)
    }
  }
}
</script>

<style scoped>
.temp{
  margin:2%;
  font-family: sans-serif;
  text-align:center;
  font-size: 23px;
  background-color: #EAECEE ;
  position: relative;
}
.label{
  padding-right: 2%;
  font-weight: bold;
}
.input{
  border-radius: 4px%;
  padding:5px 12px;
  width:20%;
  padding:.6%;
 }
#preview{
  padding:5px 12px;
  margin:30px 0;
  border:1px;
  margin-left: 40%
}
.button {
  padding:5px;
  width:7%;
  border-radius: 4px%;
  font-size:15px;
}
.error{
  font-family: 'Lucida Sans';
  color: red;
  font-size: 17px;
  text-align: center
}
/*
 input:invalid {
  border: 8px solid red;
} */
input:hover, input:active {
  font-family: monospace;
  border: 2px solid black;
}
.preview {
  font-family: fantasy;
  font-size: 20px;
  padding-left: 2%;
  margin:1%;
}
#data {
  padding-left:7%;
  font-size: 25px;
  color: rgb(103, 121, 167)
}
#hobby {
  /* padding-top:10px; */
  padding-right: 1.2%;
  font-size: 20px;
}
#checkbox {
  width: 1.5em;
  height: 1.3em;
  background-color: white;
  border-radius: 50%;
  vertical-align: middle;
  border: 1px solid #ddd;
  -webkit-appearance: none;
  outline: none;
  cursor: pointer;
  /* outline: .5px solid black; */
}
#checkbox:checked {
  background-color: rgb(103, 121, 167);
}
input[type='radio']:after {
        width: 15px;
        height: 15px;
        border-radius: 15px;
        top: -2px;
        left: -1px;
        position: relative;
        background-color: #d1d3d1;
        content: '';
        display: inline-block;
        visibility: visible;
        border: 2px solid white;
    }
    input[type='radio']:checked:after {
        width: 15px;
        height: 15px;
        border-radius: 15px;
        top: -2px;
        left: -1px;
        position: relative;
        background-color: rgb(103, 121, 167);
        content: '';
        display: inline-block;
        visibility: visible;
        /* border: 2px solid white; */
    }
</style>
