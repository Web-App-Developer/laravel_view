<template>
<div>
    <div v-if="!$root.isMobile">
        <div class="home col-5 mx-auto py-5 mt-5">
            <h1 class="text-center">Register</h1>
            <div class="card">
                <div class="card-body">
                    <div class="form-group">
                        <label for="name">First Name:</label>
                        <input type="text" v-model="form.first_name" class="form-control" id="first_name" />
                        <span class="text-danger" v-if="errors.first_name">
                            {{ errors.first_name[0] }}
                        </span>
                    </div>
                    <div class="form-group">
                        <label for="last_name">Last Name:</label>
                        <input type="text" v-model="form.last_name" class="form-control" id="last_name" />
                        <span class="text-danger" v-if="errors.last_name">
                            {{ errors.last_name[0] }}
                        </span>
                    </div>
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
                    <div class="form-group">
                        <label for="password_confirmation">Confirm Password:</label>
                        <input type="password" v-model="form.password_confirmation" class="form-control" id="password_confirmation" />
                        <span class="text-danger" v-if="errors.password_confirmation">
                            {{ errors.password_confirmation[0] }}
                        </span>
                    </div>
                    <button type="submit" @click.prevent="register" class="btn btn-primary btn-block">
                        Register
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
            <h5 class="text-center login-title">Create your free account</h5>
        </div>
        <form class="row no-gutters pw-5">

            <div class="col-6">
                <div class="form-group p-1">
                    <input class="form-control register-form-control" placeholder="First name" type="text" />
                </div>
            </div>

            <div class="col-6">
                <div class="form-group p-1">
                    <input class="form-control register-form-control" placeholder="Last name" type="text" />
                </div>
            </div>
            <div class="col-12">
                <div class="form-group p-1">
                    <input class="form-control register-form-control" placeholder="Email Address" type="text" />
                </div>
            </div>

            <div class="col-6">
                <div class="form-group p-1">
                    <input class="form-control register-form-control" placeholder="Password" type="password" />
                </div>
            </div>

            <div class="col-6">
                <div class="form-group p-1">
                    <input class="form-control register-form-control" placeholder="Confirm Password" type="confirm_password" />
                </div>
            </div>

            <div class="col-12">
                <div class="g-recaptcha" data-sitekey="6Lel4Z4UAAAAAOa8LO1Q9mqKRUiMYl_00o5mXJrR"></div>
            </div>

            <div class="col-12 flex">
                <div class="form-group p-1 mt-5">
                    <button class="btn btn-block purple signup">Sign Up</button>
                </div>
            </div>
        </form>
        <div class="register-footer-area">
            <h6 class="text-center footer-title">Already have an account? &nbsp;<a href="#" class="puple">Login</a></h6>
            <h6 class="text-center footer-title">
              By joining your agree to to the <a href="#" class="Terms">Terms</a> and <a href="#" class="">Privacy Policy</a></h6>
        </div>
    </div>
</div>
</template>

<script src="https://www.google.com/recaptcha/api.js" async defer></script><script>
import User from "../../apis/User";

export default {
    data() {
        return {
            form: {
                name: "",
                email: "",
                password: "",
                password_confirmation: ""
            },
            errors: []
        };
    },

    methods: {
        register() {
            User.register(this.form)
                .then(() => {
                    this.$router.push({
                        name: "Login"
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
