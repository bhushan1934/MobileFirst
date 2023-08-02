<template>
  <div class="container">
    <form @submit.prevent="login">
      <h2 class="mb-3">Login</h2>
      <div class="input">
        <label for="email">Email address</label>
        <input
          class="form-control"
          type="text"
          name="email"
           v-model="form.email"
          placeholder="email@adress.com"
        />
      </div>
      <div class="input">
        <label for="password">Password</label>
        <input
          class="form-control"
          type="password"
          name="password"
           v-model="form.password"
          placeholder="password123"
        />
      </div>
      <div class="alternative-option mt-4">
        You don't have an account? <span @click="moveToRegister">Register</span>
      </div>
      <button type="submit" class="mt-4 btn-pers" id="login_button">
        Login
      </button>
      <div
        class="alert alert-warning alert-dismissible fade show mt-5 d-none"
        role="alert"
        id="alert_1"
      >
        Lorem ipsum dolor sit amet consectetur, adipisicing elit.
        <button
          type="button"
          class="btn-close"
          data-bs-dismiss="alert"
          aria-label="Close"
        ></button>
      </div>
    </form>
  </div>
</template>

<script>
	import { reactive, inject,ref, onMounted } from 'vue';
	import axios from 'axios';
	export default{
       methods: {
    moveToRegister(){
      this.$router.push("maps");
    },
   
  },
  
		setup(){
			let cookies = inject('cookies')
			let isAuthenticated = ref(false)
			const form = reactive({
				email:'',
				password:''
			});

			const login = async()=>{
				let res = await axios.post('http://127.0.0.1:8000/api/login',form)
        console.log(res.data);
				if(res.data.token){
					cookies.set('access_token',res.data.token)
					isAuthenticated.value = true
             redirectToDashboard(); // Redirect to the dashboard
      } else {
        showAlert(); // Show alert if login fails
      }
				}


    
			const checkLogin = ()=>{
				if(cookies.get('access_token')){
					isAuthenticated.value = true;
				}
			}

			const logout = () =>{
				if(cookies.get('access_token')){
					cookies.set('access_token','')
					isAuthenticated.value = false;
				}
			}

			onMounted(checkLogin)

			return {
				form,
				login,
				isAuthenticated,
				logout
			}
     
		}
  
	}
  
</script>