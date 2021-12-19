<template>
  <div class="Register">
    <div class="row">
    	<div class="col-lg-4 mx-auto border shadow rounded p-4 mt-3">
    		<h1 class="mt-3 mb-4 text-center">Register</h1>
    		<hr>
		    <form @submit.prevent="doRegister">
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
			  <div class="form-group">
			    <label for="passwordInput2">Repeat Password</label>
			    <input
			    	type="password"
			    	class="form-control"
			    	id="passwordInput2"
			    	v-model="password2"
			    	:class="{
			    		'is-invalid':password2Error===true,
			    		'is-valid':password2Error===false}">
			    	<div class="invalid-feedback" v-if="password2Error">
    					{{password2ErrorMessage}}
  					</div>
			  </div>
			  <button type="submit" class="btn btn-primary btn-block mt-4" >Register</button>
			</form>
    	</div>
    </div>
  </div>
</template>

<script>
	export default {
		name: 'Register',

		data() {
			return {
				username : '',
				password : '',
				password2 : '',
				usernameError: null,
				passwordError: null,
				password2Error: null,
				usernameErrorMessage: null,
				passwordErrorMessage: null,
				password2ErrorMessage: null,
			}
		},

		methods: {
			doRegister() {
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

				if (this.password2.length < 6) {
					access = false
					this.password2Error = true
					if (this.password2.length == 0) {
						this.password2ErrorMessage = 'Repeat password required.'
					} else {
						this.password2ErrorMessage = 'Repeat password must be at least 6 characters long.'
					}
				} else {
					this.password2Error = false
					this.password2ErrorMessage = ''
				}

				if (this.password != this.password2) {
					access = false
					this.passwordError = true
					this.password2Error = true
					this.passwordErrorMessage = "Password aren't same."

				} else {
					if (!this.passwordErrorMessage && !this.password2ErrorMessage) {
						this.passwordErrorMessage = ""
					}
				}
				



				if (access) {
					this.$store.commit('login', `${this.username}:${this.password}`)
					this.$router.push('/Profile')
				}
				
			}
		}
	}
</script>