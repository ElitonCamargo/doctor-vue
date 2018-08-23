<template>
    <v-content>
        <v-container>
            <v-layout align-center justify-center>
                <v-flex md5>
                    Login
                    <v-form>
                        <v-text-field v-model="email">
                            
                        </v-text-field>
                        <v-text-field v-model="password">

                        </v-text-field>
                    </v-form>
                    <v-btn @click.stop="loginUser()"> Login </v-btn>
                </v-flex>
            </v-layout>
        </v-container>
    </v-content>
</template>

<script>
import { auth } from 'firebase'
export default {
    mame: 'login',
    data(){
        return{
            email: '',
            password: '',
        }
    },
    methods: {
        async loginUser(){
            try {
                const User = await firebase.auth().signInWithEmailAndPassword(this.email, this.password)
                alert(`Logged in ${User.user.email}`) 
                this.$router.push('/') 
            } catch (error) {
                alert(error.message)
            }
        }
    }
}
</script>
