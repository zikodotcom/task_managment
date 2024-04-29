<script setup>
    import axios from 'axios'
    import {ref, onMounted} from 'vue';
    let email = ref('')
    let password = ref('')
    let fullName = ref('')
    let passwordConfirm = ref('')
    let fullNameRules = [
        value => {
            if(value) return true
            return 'Full name is required.'
        },
        value => {
            if(value.length >= 10) return true
            return 'The full name should be more than 9 charachters.'
        }
    ]
    let enailRules = [
        value => {
            if(value) return true
            return 'E-mail is required.'
        },
        value => {
          if (/.+@.+\..+/.test(value)) return true

          return 'E-mail must be valid.'
        }
    ]
    let passwordRules = [
        value => {
            if(value) return true;
            return 'Password is required.'
        },
        value => {
            if(value.length >= 8) return true
            return 'Password should at least contain 8 charachters.'
        }
    ]
    let confirmPasswordRules = [
        value => {
            if(value) return true;
            return 'Password confirmation is required.'
        },
        value => {
            if(value.length >= 8) return true
            return 'Password should at least contain 8 charachters.'
        },
        value => {
            if(value == password.value) return true
            return 'Password confirmation not match.'
        }
    ]
    const handleSubmit = () => {
        axios.post('http://127.0.0.1:5000/register', {fullName: fullName.value, email: email.value, password: password.value})
        .then(res => {
            console.log('is affected');
        })
        .catch(err => {
            console.log("isn't affected");
        })
    }
</script>   


<template>
    <div class="tw-flex">
        <div class="tw-w-[50%] tw-h-[100vh] tw-flex tw-flex-col tw-justify-center tw-items-center">
            <img src="@/assets/pngegg.png" alt="" class="tw-w-20 tw-h-1tw-w-20">
            <h1 class="tw-font-bold tw-text-2xl">Welcome</h1>
            <p class="tw-text-sm">Please enter your details.</p>
            <v-form @submit.prevent="handleSubmit" class="tw-w-[100%] tw-flex tw-flex-col tw-items-center tw-justify-center">
                <v-container>
                    <v-row>
                        <v-col md="3"></v-col>
                        <v-col        
                        class="!tw-p-0 !tw-pl-4"             
                            cols="12"
                            md="6"
                            >
                            <label for="" class="tw-font-bold">Full name</label>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="3"></v-col>
                        <v-col         
                        class="!tw-p-0 !tw-pl-4"             
                            cols="12"
                            md="6"
                            
                        >
                            <v-text-field
                            v-model="fullName"
                            :rules="fullNameRules"
                            label="Enter your full name"
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="3"></v-col>
                        <v-col      
                        class="!tw-p-0 !tw-pl-4"             

                            cols="12"
                            md="6"
                            >
                            <label for="" class="tw-font-bold">Email</label>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="3"></v-col>
                        <v-col       
                        class="!tw-p-0 !tw-pl-4"             

                            cols="12"
                            md="6"
                            
                        >
                            <v-text-field
                            v-model="email"
                            :rules="enailRules"
                            label="Enter your email"
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="3"></v-col>
                        <v-col      
                        class="!tw-p-0 !tw-pl-4"             

                            cols="12"
                            md="6"
                            >
                            <label for="" class="tw-font-bold">Password</label>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="3"></v-col>
                        <v-col        
                        class="!tw-p-0 !tw-pl-4"             
                            cols="12"
                            md="6"
                            >
                            <v-text-field
                            v-model="password"
                            type="password"
                            :counter="8"
                            :rules="passwordRules"
                            label="Enter your password"
                            :type="show1 ? 'text' : 'password'"
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="3"></v-col>
                        <v-col      
                        class="!tw-p-0 !tw-pl-4"             

                            cols="12"
                            md="6"
                            >
                            <label for="" class="tw-font-bold">Confirm password</label>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="3"></v-col>
                        <v-col        
                        class="!tw-p-0 !tw-pl-4"             
                            cols="12"
                            md="6"
                            >
                            <v-text-field
                            v-model="passwordConfirm"
                            type="password"
                            :counter="8"
                            :rules="confirmPasswordRules"
                            label="Password confirmation"
                            :type="show1 ? 'text' : 'password'"
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col md="3"></v-col>
                        <v-col md="6">
                            <button class="
                            tw-bg-black tw-px-4 tw-py-2 tw-text-white tw-font-bold tw-border-2 tw-border-solid tw-rounded-xl  hover:tw-bg-white hover:tw-text-black hover:tw-border-2 hover:tw-border-solid hover:tw-border-black">Register</button>
                        </v-col>
                    </v-row>
                    
                </v-container>
            </v-form>
        </div>
        <div>
            <img class="tw-w-[100%] tw-h-[100vh]" src="https://t4.ftcdn.net/jpg/01/98/24/71/360_F_198247162_JwrVkhqowZb4NJC24156nV6QYRhsV8Qf.jpg" alt="">
        </div>
    </div>
</template>