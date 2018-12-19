<template>
    <div class="sign-up">
        
        <form  id="tijelo-signup" v-on:submit.prevent="signUp">
        <div></div>
        <div id="glavno-signup">
            	<div>
			  		<div></div>
			  		<div>
			  			<div class="wrap-signup-1"><p>Please fill in all information</p></div>
			  		</div>
			  		<div></div>
			  	</div>

                <div id="email-signup">
					<div></div>
						<div>
							<input id="sign-up-email" type="text" v-model="email" placeholder="Email"><br>
						</div>
					<div></div>
				</div>

                <div class="password-signup">
					<div></div>
						<div>
        					<input class="sign-up-pw" type="password" v-model="password" placeholder="Password"><br>
						</div>
					<div></div>
				</div>

                <div class="password-signup">
					<div></div>
						<div>
        					<input class="sign-up-pw" type="password" v-model="password" placeholder="Confirm password"><br>
						</div>
					<div></div>
				</div>

                <div id="btn-singup">
					<div></div>
					<div>
        				<button id="sign-up-submit" type="submit">Register</button>
					</div>
					<div></div>
				</div>

                <div id="back-to-login">
					<div></div>
					<div>
						<p><router-link to="/login">Go back to login</router-link></p>
					</div>
					<div></div>
				</div>
                
        </div>
        <div></div>
        </form>
        
    </div>
</template>
<script>
import firebase from 'firebase'
    export default{
        name: 'signUp',
        data: function() {
            return {
                email: '',
                password: ''
            }
        },
        methods: {
            signUp: function(){                
                firebase.auth().createUserWithEmailAndPassword(this.email, this.password).then(
                    (user) => {
                        this.$router.replace('home')
                    },
                    (err) => {
                        alert('Oops. ' + err.message)
                    },
                );
            }
        }
    }
</script>

<style scoped>
*{
	font-family: "Roboto";
}
#tijelo-signup{
	margin: 10% auto;
	font-family: "Roboto";
	display: grid;
	grid-template-columns: 1fr 8fr 1fr;
}

#glavno-signup{
	height: 270px;
	display: block;
	margin: auto;
	background:rgba(0, 178, 215, 0.3);
	width: 100%;
}

#email-signup, .password-signup, #btn-singup, #back-to-login {
	display: grid;
	grid-template-rows: 1fr 100% 1fr;
	height: 35px;
	margin: auto;
}

#glavno-signup button{
	
	display: block;
	margin: auto;
	background:rgb(0, 178, 215);
	color: white;
}

#glavno-signup input{
	display: block;
	margin: auto;
	height: 25px;
	border: none;
	border-radius: 3px;
	font-size: 15px;
	text-align: center;
	padding-top: 10px;
	padding-bottom: 5px;
}

.wrap-signup-1{
	
	text-align: center;
}

#glavno-signup button{
	font-weight: bold;
	height: 40px;
	width: 170px;
	display: block;
	margin: auto;
	border: none;
	margin: 10px auto;
	border-radius: 3px;
 }

 .wrap-signup-1 p{
	padding: 20px;
 	height: 10px;
 }

#back-to-login p{
	text-align: center;
	padding: 30px;
}
</style>