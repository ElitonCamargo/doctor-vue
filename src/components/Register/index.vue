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
        >
        </v-text-field>
        <v-btn 
            block
            color="cyan darken-4"
            outline
            
        >
            CADASTRAR
        </v-btn>
    </v-form>
</template>

<script>
import { auth } from 'firebase'
import { validationMixin } from 'vuelidate'
import { required, maxLength, email } from 'vuelidate/lib/validators'

export default {
    name: 'FormRegister',
    data(){
        return{
            email: '',
            password: ''
        }
    },
    mixins: [validationMixin],
    validations: {
        
    }
};
</script>
