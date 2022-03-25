<template>
    <div>
        <form class="register-form-wrapper" @submit.prevent="registerAdmin">

            <div class="register-form-title">
                <h3>Register form</h3>
            </div>

            <ul class="register-from-inputs">

                <!-- firstname -->
                <li>

                    <label for="firstname">firstname</label>
                    <input type="text" v-model="first_name.value" name="firstname" id="firstname">
                    <span>{{first_name.error}}</span>

                </li>

                <!-- lastname -->
                <li>
                    <label for="lastname">lastname</label>
                    <input type="text" v-model="last_name.value" name="lastname" id="lastname">
                    <span>{{last_name.error}}</span>

                </li>

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
    methods: {
        async registerAdmin(){
            try {
                const {
                    first_name: {
                        value:first_name
                    }, 
                    last_name: {
                        value:last_name
                    }, 
                    email: {
                        value:email
                    }, 
                    password: {
                        value:password
                    }, 
                    username: {
                        value:username
                    }, 
                } = this

                const body = {
                    first_name,
                    last_name,
                    password,
                    username,
                    email
                }

                const res = await this.$axios.post("http://localhost:8080/api/v1/admin/register", body);
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
            first_name: {
                value: '',
                error: null
            },
            last_name: {
                value: '',
                error: null
            },
            email: {
                value: '',
                error: null
            },
            password: {
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
.register-form-wrapper{
    width: 50%;
    padding: 40px;
    margin: auto;
    border: 3px solid black;
    border-radius: 15px;
}
.register-form-title  {
    margin-bottom: 20px;
    font-size: 1.2em;
}

.register-from-inputs label {
    display: inline-block;
    min-width: 100px;
}
.register-from-inputs li {
    margin: 10px;
    list-style-type: none;
}

.submit-button {
    margin: 10px;
    padding: 5px 10px;
}

.register-from-inputs{
    display: flex;
    flex-direction: column;
    justify-content: center;
}

</style>