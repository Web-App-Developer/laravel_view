<template>
<div>
    <div v-if="!$root.isMobile">
        <div class="home col-5 mx-auto py-5 mt-5">
            <h1 class="text-center">Login</h1>
            <div class="card">
                <div class="card-body">
                    <div class="form-group">
                        <label for="email">Email address:</label>
                        <input type="email" v-model="form.email" class="form-control" id="email" />
                        <span class="text-danger" v-if="errors.email">
                            {{ errors.email[0] }}
                        </span>
                    </div>
                    <div class="form-group">
                        <label for="password">Password:</label>
                        <input type="password" v-model="form.password" class="form-control" id="password" />
                        <span class="text-danger" v-if="errors.password">
                            {{ errors.password[0] }}
                        </span>
                    </div>
                    <button @click.prevent="login" class="btn btn-primary btn-block">
                        Login
                    </button>
                </div>
            </div>
        </div>
    </div>
    <div v-else>
        <div class="login-logo-area">
            <img class="login-logo" :src="$root.storageUrl+'/images/artigram-logo.png'" />
        </div>
        <div class="login-title-area">
            <h1 class="text-center login-title">Login</h1>
            <div class="login-subtitle-area">
                <h5 class="login-subtitle-top">Generate an instant store from any image.</h5>
                <h5 class="login-subtitle-buttom">Empower your Fans</h5>
            </div>
        </div>
        <div class="login-container">
            <form class="login-form">
                <div class="input-field">
                    <!-- <label htmlFor="email" class="lbl-email">E-Mail address</label> -->
                    <input placeholder="E-Mail address" type="text" name="email" class="validate email" required />
                </div>
                <div class="input-field">
                    <!-- <label htmlFor="password" class="lbl-password">Password</label> -->
                    <input placeholder="Password" type="password" name="password" class="validate password" required />
                </div>
                <div class="input-field forget">
                    <h5 class="forgot-password">Forgot Password?</h5>
                </div>

                <div class="input-field remember">

                    <label class="remember-text" for="remember-text">
                        <input type="checkbox" class="checkbox">Remember Me
                    </label>
                </div>
                <div class="input-field btn-area">
                    <button class="login-submit" type='submit'>Log in</button>
                </div>
                <div class="input-field apply-area">
                    <h6 class="apply">Don't have an account &nbsp; <a class="puple" href="#">Apply for an account</a></h6>
                </div>
            </form>
        </div>
    </div>

</div>
</template>

<script>
import User from "../../apis/User";

export default {
    data() {
        return {
            form: {
                email: "",
                password: ""
            },
            errors: []
        };
    },

    methods: {
        login() {
            User.login(this.form)
                .then(() => {
                    this.$root.$emit("login", true);
                    localStorage.setItem("auth", "true");
                    this.$router.push({
                        name: "Dashboard"
                    });
                })
                .catch(error => {
                    if (error.response.status === 422) {
                        this.errors = error.response.data.errors;
                    }
                });
        }
    }
};
</script>
