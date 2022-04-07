<template>
	<form @submit.prevent="handleSubmit">
		<label>Email</label>
		<input type="email" required v-model="email" />

		<label>Password</label>
		<input type="password" required v-model="password" />
        <div v-if="passwordError" class="error">{{ passwordError }}</div>

		<label>Role</label>
		<select v-model="role">
			<option value="developer">Web Developer</option>
			<option value="designer">Web Designer</option>
		</select>

		<label>Skills</label>
		<input type="text" v-model="tempSkill" @keyup="addSkill" @keypress="preventSubmit" />
		<div v-for="skill in skills" :key="skill" class="pill">
			<span @click="deleteSkill(skill)"> {{ skill }} &times; </span>
		</div>

		<div class="terms">
			<input type="checkbox" v-model="terms" required />
			<label>Accept terms and conditions</label>
		</div>

		<div class="submit">
			<button>Create Account</button>
		</div>

		<!-- <div>
            <input type="checkbox" value="billy" v-model="names"/>
            <label>Billy</label>
        </div>
        <div>
            <input type="checkbox" value="vero" v-model="names"/>
            <label>Vero</label>
        </div>
        <div>
            <input type="checkbox" value="veril" v-model="names"/>
            <label>Veril</label>
        </div> -->
	</form>
	<p>Email: {{ email }}</p>
	<p>Password: {{ password }}</p>
	<p>Role: {{ role }}</p>
	<p>Terms accepted: {{ terms }}</p>
	<p>Temp Skill: {{ skills }}</p>
	<!-- <p>Names: {{ names }}</p> -->
</template>

<script>
	export default {
		data() {
			return {
				email: "",
				password: "",
				role: "",
				terms: false,
				tempSkill: "",
				skills: [],
                passwordError: ''
				// names: []
			};
		},
		methods: {
			addSkill(e) {
				if (e.key === "Enter" && this.tempSkill) {
					if (!this.skills.includes(this.tempSkill)) {
						this.skills.push(this.tempSkill);
					}
					this.tempSkill = "";
				}
			},

			deleteSkill(name) {
				this.skills = this.skills.filter((item) => {
					return name !== item;
				});
			},

            handleSubmit(e){
                this.passwordError = this.password.length > 5 ? '' : 'Password must be at least 6 chars long'

                if(!this.passwordError){
                    // console.log('submitted!')
                    console.log('email: ' + this.email)
                    console.log('password: ' + this.password)
                    console.log('role: ' + this.role)
                    console.log('skills: ' + this.skills)
                    console.log('terms accepted: ' + this.terms)
                }
            },

            preventSubmit(e){
                var key = e.charCode || e.keyCode || 0;     
                if (key == 13) {
                    e.preventDefault();
                }
            }
		},
	};
</script>

<style scoped>
	form {
		max-width: 420px;
		margin: 30px auto;
		background: white;
		text-align: left;
		padding: 40px;
		border-radius: 10px;
	}
	label {
		color: #aaa;
		display: inline-block;
		margin: 25px 0 15px;
		font-size: 0.6em;
		text-transform: uppercase;
		letter-spacing: 1px;
		font-weight: bold;
	}

	input,
	select {
		display: block;
		padding: 10px 6px;
		width: 100%;
		box-sizing: border-box;
		border: none;
		border-bottom: 1px solid #ddd;
		color: #555;
	}

	input:focus,
	select:focus {
		outline: none;
		border-bottom: 1px solid #346;
	}

	input[type="checkbox"] {
		display: inline-block;
		width: 16px;
		margin: 0 10px 0 0;
		position: relative;
		top: 2px;
	}

	.pill {
		display: inline-block;
		margin: 20px 10px 0 0;
		padding: 6px 12px;
		background: rgb(54, 106, 237);
		border-radius: 12px;
		letter-spacing: 1px;
		font-weight: bold;
		color: #fff;
		cursor: pointer;
	}

	.submit {
		text-align: center;
	}

	button {
		background: #0b6dff;
		border: 0;
		padding: 10px 20px;
		margin-top: 20px;
		color: #fff;
		border-radius: 20px;
		cursor: pointer;
		font-weight: 600;
	}

    .error{
        font-size: 12px;
        color: crimson;
        font-weight: 400;
    }
</style>