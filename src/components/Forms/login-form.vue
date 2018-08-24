<template>
    <v-container grid-list-md>
        <v-layout>
            <v-flex xs12>
                <v-tabs
                    color="cyan darken-2"
                    dark
                    
                    grow
                    slider-color="white"
                >
                    <v-tab>
                        ENTRAR
                    </v-tab>
                    <v-tab>
                        CADASTRE-SE
                    </v-tab>
                    <v-tab-item>
                        <FormLogin />
                    </v-tab-item>
                    <v-tab-item>
                        <RegisterForm />
                    </v-tab-item>
                </v-tabs>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
import FormLogin from '@/components/Login'
import RegisterForm from '@/components/Register'
export default {
    name: 'loginform',
    components: {
        FormLogin,
        RegisterForm
    }
}
</script>
