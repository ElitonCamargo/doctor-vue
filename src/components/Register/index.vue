<template>
    <v-form>
        <v-text-field
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
            prepend-icon="lock"
            v-model="password"
            type="Password"
            label="Senha"
            :error-messages="passwordErrors"
            @input="$v.password.$touch()"
            @blur="$v.password.$touch()"
        >
        </v-text-field>
        <v-text-field
            prepend-icon="lock"
            v-model="confPass"
            type="Password"
            label="Confirmar Senha"
            :error-messages="confErrors"
            @input="$v.confPass.$touch()"
            @blur="$v.confPass.$touch()"
        >

        </v-text-field>
        <v-btn 
            block
            color="cyan darken-4"
            outline
            @click.stop="userRegister()"
        >
            CADASTRAR
        </v-btn>
        <v-layout class="alertErro">
            dasidjoasidasidjoasidasidjoasidasidjoasi
            dasidjoasidasidjoasidasidjoasidasidjoasi
            dasidjoasidasidjoasidasidjoasidasidjoasi
            dasidjoasidasidjoasidasidjoasidasidjoasi
            dasidjoasidasidjoasidasidjoasidasidjoasi
        </v-layout>
    </v-form>
</template>

<script>
import { auth } from 'firebase'
import { validationMixin } from 'vuelidate'
import { required, minLength, sameAs ,email } from 'vuelidate/lib/validators'
export default {
    name: 'FormRegister',
    data(){
        return{
            email: '',
            password: '',
            confPass: ''
        }
    },
    mixins: [validationMixin],
    validations: {
        email: { required, email },
        password: { required, minLength: minLength(4)},
        confPass: { required, sameAsPassword: sameAs('password')}
        
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
            !this.$v.password.minLength && errors.push('Minimo de 4 digitos')
            return errors
        },
        confErrors () {
            const errors = []
            if(!this.$v.confPass.$dirty) return errors
            !this.$v.confPass.required && errors.push('Confirmar senha é obrigatório')
            !this.$v.confPass.sameAsPassword && errors.push('As senhas não conhecidem')
            return errors
        }
    },
    methods:{
        async userRegister(){
            this.$v.$touch()
            if(this.$v.$invalid){
            }else {
            }
        }
    }
};
</script>

<style>
    .alertErro{
        position: fixed;
        background-color: black;
        bottom: 0;
    }
</style>
