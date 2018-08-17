<template>
    <v-toolbar
        color="blue darken-2"
        flat
        absolute
        app
    >
        <v-layout
            align-center
            justify-center
        >
            <v-flex md6 sm8>
                <v-form 
                >
                    <v-text-field
                        solo
                        class="mt-1"
                        label="Nome / CRM"
                        append-icon="search"
                    >
                    </v-text-field>
                </v-form>
            </v-flex>
        </v-layout>
    </v-toolbar>
</template>

<script>
export default {
    name: 'Toolbar'
}
</script>
