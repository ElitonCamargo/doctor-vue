<template>
    <v-content>
        <v-container fluid>
            <v-layout
                align-center
                justify-center
                dark
            >
                <v-flex xs10>
                    
                </v-flex>
            </v-layout>
        </v-container>
        <FormLogin v-if="form"/>      
    </v-content>
</template>

<script>
import FormLogin from '@/components/Forms/login-form'
import db from '@/firebase/firebaseinit.js'
export default {
    name: "Home",
    data() {
        return {
            form: false
        }
    },
    components: {
        FormLogin
    }
}
</script>
