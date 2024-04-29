<template>
    <div class="flex">
        <div>
            <img src="@/assets/pngegg.png" alt="">
            <h1>Welcome back</h1>
            <p>Please enter your details.</p>
            <v-form v-model="valid">
                <v-container>
                    <v-row>
                        <v-col                            
                            cols="12"
                            md="4">
                            <label for="">Email</label>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col
                            cols="12"
                            md="4"
                        >
                            <v-text-field
                            v-model="firstname"
                            :counter="10"
                            :rules="nameRules"
                            label="First name"
                            hide-details
                            required
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col                            
                            cols="12"
                            md="4">
                            <label for="">Password</label>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-col                            
                            cols="12"
                            md="4">
                            <v-text-field
                            v-model="firstname"
                            :counter="10"
                            :rules="nameRules"
                            label="First name"
                            hide-details
                            required
                            ></v-text-field>
                        </v-col>
                    </v-row>
                    <button>Submit</button>
                </v-container>
            </v-form>
        </div>
        <div>
            <img src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*PWdG4Rs528yuQgIOY0b8-g.jpeg" alt="">
        </div>
    </div>
</template>