<template>
    <div>
        <form class="authenticate-form-wrapper" @submit.prevent="authenticateAdmin">

            <div class="register-form-title">
                <h3>authenticate form</h3>
            </div>

            <ul class="authenticate-from-inputs">

                <!-- password -->
                <li>

                    <label for="password">password</label>
                    <input type="password" v-model="password.value" name="password" id="password">
                    <span>{{password.error}}</span>

                </li>

                
                
            </ul>
            

            <input type="submit" value="submit" class="submit-button" id="submit">


        </form>
    </div>
</template>

<script>
export default {
    name: "PasswordValidation",
    methods: {
        async authenticateAdmin(){
            try {
                const {
                    password: {
                        value:password
                    }, 
                    
                } = this

                const {username, email, token:authorization} = this.authData;

                const body = {
                    password,
                    username,
                    email,
                }

                const headers = {
                    authorization
                }

                const url = '/admin/authenticate'
                
                const res = await this.$axios.post(url, body, {
                    withCredentials: true,
                    headers
                });
                console.log(res);
                console.log(res.data);
            } catch (error) {
                console.log(error.message);
            }
        },
    },
    data() {
        return{
            password: {
                value: '',
                error: null
            },
        }
    },
    props: [
        "authData"
    ]

}
</script>

<style >
.authenticate-form-wrapper{
    width: 50%;
    padding: 40px;
    margin: auto;
    border: 3px solid black;
    border-radius: 15px;
}
.authenticate-form-title  {
    margin-bottom: 20px;
    font-size: 1.2em;
}

.authenticate-from-inputs label {
    display: inline-block;
    min-width: 100px;
}
.authenticate-from-inputs li {
    margin: 10px;
    list-style-type: none;
}

.submit-button {
    margin: 10px;
    padding: 5px 10px;
}

.authenticate-from-inputs{
    display: flex;
    flex-direction: column;
    justify-content: center;
}

</style>