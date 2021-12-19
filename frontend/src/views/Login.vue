<template>
  <div class="login">
    <div class="row">
    	<div class="col-lg-4 mx-auto border shadow rounded p-4 mt-3">
    		<h1 class="mt-3 mb-4 text-center">Login</h1>
    		<hr>
		    <form @submit.prevent="doLogin">
			  <div class="form-group">
			    <label for="usernameInput">User Name</label>
			    <input
			    	type="text"
			    	class="form-control"
			    	id="usernameInput"
			    	v-model="username"
			    	:class="{
			    		'is-invalid':usernameError===true,
			    		'is-valid':usernameError===false}">
			    	<div class="invalid-feedback" v-if="usernameError">
    					{{usernameErrorMessage}}
  					</div>
			  </div>
			  <div class="form-group">
			    <label for="passwordInput">Password</label>
			    <input
			    	type="password"
			    	class="form-control"
			    	id="passwordInput"
			    	v-model="password"
			    	:class="{
			    		'is-invalid':passwordError===true,
			    		'is-valid':passwordError===false}">
			    	<div class="invalid-feedback" v-if="passwordError">
    					{{passwordErrorMessage}}
  					</div>
			  </div>
			  <button type="submit" class="btn btn-primary btn-block mt-4" >Login</button>
			</form>
    	</div>
    </div>
  </div>
</template>

<script>
	export default {
		name: 'Login',

		data() {
			return {
				username : '',
				password : '',
				usernameError: null,
				passwordError: null,
				usernameErrorMessage: null,
				passwordErrorMessage: null,
			}
		},

		methods: {
			doLogin() {
				let access = true

				if (this.username.length < 5) {
					access = false
					this.usernameError = true
					if (this.username.length == 0) {
						this.usernameErrorMessage = 'Username required.'
					} else {
						this.usernameErrorMessage = 'Username must be at least 5 characters long.'
					}
				} else {
					this.usernameError = false
					this.usernameErrorMessage = ''
				}

				if (this.password.length < 6) {
					access = false
					this.passwordError = true
					if (this.password.length == 0) {
						this.passwordErrorMessage = 'Password required.'
					} else {
						this.passwordErrorMessage = 'Password must be at least 6 characters long.'
					}
				} else {
					this.passwordError = false
					this.passwordErrorMessage = ''
				}
				
				if (access) {
					this.$store.commit('login', `${this.username}:${this.password}`)
					this.$router.push('/Profile')
				}
				
			}
		}
	}
</script>