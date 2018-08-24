<template>
    <v-toolbar
        color="cyan"
        flat
        app
        height="70vh"
    >
        <v-toolbar-items class="ma-1 pr-2">
                <v-icon dark>
                    face
                </v-icon>
        </v-toolbar-items>
        <v-layout
            align-center
            justify-center
        >
            <v-flex md8 sm8 xs12>
                <v-form 
                >
                    <v-text-field
                        dark
                        class="pt-3 ma-3"
                        label="Nome / CRM"
                        append-icon="search"
                    >
                    </v-text-field>
                </v-form>
            </v-flex>
        </v-layout>
        <v-toolbar-items>
            <v-btn
                dark
                flat
                left
                @click.stop="openDialog()"
            >
                <v-icon>
                    account_circle
                </v-icon>
                Login
            </v-btn>
        </v-toolbar-items>
        <v-dialog
            v-model="dialog"
            max-width="500pt"
        >
            <v-card>
                <FormLR/>
            </v-card>
        </v-dialog>
    </v-toolbar>
</template>

<script>
import FormLR from '@/components/Forms/login-form'
export default {
    name: 'Toolbar',
    data(){
        return{
            dialog: false
        }
    },
    components: {
        FormLR
    },
    methods:{
        openDialog(){
            this.dialog = true
        }
    }
}
</script>
