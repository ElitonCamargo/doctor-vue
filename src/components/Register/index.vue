<template>
    <v-content>
        <v-container>
            <v-layout align-center justify-center>
                <v-flex md5>
                    Register
                    <v-form>
                        <v-text-field v-model="email">
                            
                        </v-text-field>
                        <v-text-field v-model="password">

                        </v-text-field>
                    </v-form>
                    <v-btn @click.stop="registerUser()"> Register </v-btn>
                </v-flex>
            </v-layout>
        </v-container>
    </v-content>
</template>

<script>
import firebase from 'firebase'
export default {
    mame: 'register',
    data(){
        return{
            email: '',
            password: ''
        }
    },
    methods: {
        async registerUser(){
            try {
                const User = await firebase.auth().createUserWithEmailAndPassword(this.email, this.password)
                alert(`User ${User.user.email} created`)     
                this.$router.push('/')       
            } catch (error) {
                alert(error.message)
            }
        }
    }
}
</script>
