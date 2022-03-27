<template>
    <div>
        <form class="login-form-wrapper" @submit.prevent="loginAdmin">

            <div class="register-form-title">
                <h3>Login form</h3>
            </div>

            <ul class="login-from-inputs">

                <!-- username -->
                <li>

                    <label for="username">username</label>
                    <input type="text" v-model="username.value" name="username" id="username">
                    <span>{{username.error}}</span>

                </li>

                <!-- email -->
                <li>

                    <label for="email">email</label>
                    <input type="email" v-model="email.value" name="email" id="email">
                    <span>{{email.error}}</span>

                </li>

                
                
            </ul>
            

            <input type="submit" value="submit" class="submit-button" id="submit">


        </form>
    </div>
</template>

<script>
export default {
    methods: {
        async loginAdmin(){
            try {
                const {
                    email: {
                        value:email
                    }, 
                    username: {
                        value:username
                    }, 
                } = this

                const body = {
                    username,
                    email
                }
                const headers = {}

                const config = {
                    headers,
                    ...body
                }

                const url = '/admin/login'
                
                const res = await this.$axios.post(url, config);
                this.$router.push('/checkMail');
                console.log(res.data);
            } catch (error) {
                console.log(error.message);
            }
        },
    },
    data() {
        return{
            username: {
                value: '',
                error: null
            },
            email: {
                value: '',
                error: null
            }
        }
    },
    props: [
        "yo"
    ]

}
</script>

<style >
.login-form-wrapper{
    width: 50%;
    padding: 40px;
    margin: auto;
    border: 3px solid black;
    border-radius: 15px;
}
.login-form-title  {
    margin-bottom: 20px;
    font-size: 1.2em;
}

.login-from-inputs label {
    display: inline-block;
    min-width: 100px;
}
.login-from-inputs li {
    margin: 10px;
    list-style-type: none;
}

.submit-button {
    margin: 10px;
    padding: 5px 10px;
}

.login-from-inputs{
    display: flex;
    flex-direction: column;
    justify-content: center;
}

</style>