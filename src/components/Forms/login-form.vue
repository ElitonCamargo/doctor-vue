<template>
    <v-container grid-list-md>
        <v-layout>
            <v-flex xs12>
                <v-tabs
                    color="cyan darken-2"
                    dark
                    fixed-tabs
                    grow
                    slider-color="cyan"
                >
                    <v-tab>
                        ENTRAR
                    </v-tab>
                    <v-tab>
                        CADASTRE-SE
                    </v-tab>
                    <v-tab-item>
                        <v-form>
                            <v-text-field
                                prepend-icon="mail"
                                v-model="email"
                                :rules="emailRules"
                                label="Email"
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
                                :rules="passRules"
                                color="cyan"
                                dark
                            >
                                Login
                            </v-btn>
                        </v-form>
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
