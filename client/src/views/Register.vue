<template>
  <div>
    <div class="offset-md-4" style="padding-top : 100px;" id="login-form">
      <div class="myform form">
        <div class="logo mb-3">
          <div class="col-md-12 text-center">
            <h1>Login</h1>
          </div>
        </div>
        <form name="login" style="height: 440px;" @submit.prevent="LoginUser">
           <div class="form-group">
            <label for="exampleInputEmail1">Username</label>
            <input
              type="text"
              name="username"
              class="form-control"
              placeholder="Enter username"
              v-model="username"
            />
          </div>
          <div class="form-group">
            <label for="exampleInputEmail1">Email address</label>
            <input
              type="email"
              name="email"
              class="form-control"
              id="email"
              aria-describedby="emailHelp"
              placeholder="Enter email"
              v-model="email"
            />
          </div>
          <div class="form-group">
            <label for="exampleInputEmail1">Password</label>
            <input
              type="password"
              name="password"
              id="password"
              class="form-control"
              aria-describedby="emailHelp"
              placeholder="Enter Password"
              v-model="password"
            />
          </div>
          <div class="form-group">
            <p class="text-center">
              By signing up you accept our
              <a href="#">Terms Of Use</a>
            </p>
          </div>
          <div class="col-md-12 text-center">
            <button type="submit" class="btn btn-block mybtn btn-primary tx-tfm">Login</button>
          </div>
          <div class="col-md-12">
            <div class="login-or">
              <hr class="hr-or" />
              <span class="span-or">or</span>
            </div>
          </div>
          <div class="col-md-12 mb-4"></div>
          <div class="form-group">
            <p class="text-center">
              Don't have account?
              <!-- <a href="#" id="signup" @click="pindahPage">Sign up here</a> -->
            </p>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    data (){
        return {
            username : '',
            email : '',
            password : ''
        }
    },
    created (){
        if(localStorage.getItem('token')){
            this.$router.push('/')
        }
    },
    methods : {
        LoginUser (){
            let {email , password , username} = this
            this.$store.dispatch('registerUser' , {email,password , username})
            .then(data=>{
                this.$router.push('/login');
            })
            .catch(console.log)
        }
    }
};
</script>

<style>
a {
  text-decoration: none !important;
}
h1,
h2,
h3 {
  font-family: "Kaushan Script", cursive;
}
.myform {
  position: relative;
  display: -ms-flexbox;
  display: flex;
  padding: 1rem;
  -ms-flex-direction: column;
  flex-direction: column;
  width: 100%;
  pointer-events: auto;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 1.1rem;
  outline: 0;
  max-width: 500px;
}
.tx-tfm {
  text-transform: uppercase;
}
.mybtn {
  border-radius: 50px;
}

.login-or {
  position: relative;
  color: #aaa;
  margin-top: 10px;
  margin-bottom: 10px;
  padding-top: 10px;
  padding-bottom: 10px;
}
.span-or {
  display: block;
  position: absolute;
  left: 50%;
  top: -2px;
  margin-left: -25px;
  background-color: #fff;
  width: 50px;
  text-align: center;
}
.hr-or {
  height: 1px;
  margin-top: 0px !important;
  margin-bottom: 0px !important;
}
.google {
  color: #666;
  width: 100%;
  height: 40px;
  text-align: center;
  outline: none;
  border: 1px solid lightgrey;
}
form .error {
  color: #ff0000;
}
#second {
  display: none;
}
</style>