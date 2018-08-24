<template>
    <v-form>
        <v-text-field
            class="pt-1"
            prepend-icon="mail"
            v-model="email"
            label="Email"
            :error-messages="emailErrors"
            @input="$v.email.$touch()"
            @blur="$v.email.$touch()"
            required
        >
        </v-text-field>
        <v-text-field
            class="pt-1"
            prepend-icon="lock"
            v-model="password"
            type="Password"
            label="Senha"
            :error-messages="passwordErrors"
            @input="$v.password.$touch()"
            @blur="$v.password.$touch()"
        >
        </v-text-field>
        <v-btn 
            block
            color="cyan darken-4"
            outline
            @click.stop="userLogin()"
        >
            LOGIN
        </v-btn>
        <v-snackbar
            v-model="alert"
            :top="true"
            :color="alertColor"
            :timeout="2000"
            :multi-line="true"
        >
            {{alertMessage}}

            <v-icon>
                {{alertIcon}}
            </v-icon>
        </v-snackbar>
    </v-form>
</template>

<script>
import firebase from 'firebase'
import { validationMixin } from 'vuelidate'
import { required, minLength, email } from 'vuelidate/lib/validators'
export default {
    name: 'FormLogin',
    data(){
        return{
            email: '',
            password: '',
            confPass: '',
            alert: false,
            alertMessage: '',
            alertColor: '',
            alertIcon: 'warning'
        }
    },
    mixins: [validationMixin],
    validations: {
        email: { required, email },
        password: { required, minLength: minLength(6)}
        
    },
    computed:{
        emailErrors () {
            const errors = []
            if(!this.$v.email.$dirty) return errors
            !this.$v.email.email && errors.push('Email Precisa ser Valido!')
            !this.$v.email.required && errors.push('Email é obrigatório')
            return errors
        },
        passwordErrors () {
            const errors = []
            if(!this.$v.password.$dirty) return errors
            !this.$v.password.required && errors.push('Senha obrigatória')
            !this.$v.password.minLength && errors.push('Minimo de 6 digitos')
            return errors
        }
    },
    methods:{
        async userLogin(){
            this.$v.$touch()
            if(this.$v.$invalid){
                this.alertColor = 'red'
                this.alertMessage = 'Preencha os campos corretamente'
                this.alert = true
            }else {
                try {
                    const user = await firebase.auth().signInWithEmailAndPassword(this.email, this.password)
                    this.alertColor = 'green'
                    this.alertIcon = 'info'
                    this.alertMessage = `Succes!`
                    this.alert = true
                } catch (error) {
                    this.alertIcon = 'warning'
                    this.alertColor = 'red'
                    this.alertMessage = error.message
                    this.alert = true
                }
            }
        }
    }
}
</script>
