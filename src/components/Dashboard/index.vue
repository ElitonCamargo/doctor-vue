<template>
    <v-content>
        <v-container
            fluid
            grid-list-lg
        >
            <v-layout wrap justify-center align-center>
                <v-flex xs10>
                    <v-card
                        color="cyan"
                        class="white--text"
                    >
                        <v-layout>
                            <v-flex xs2>
                                <v-img
                                    :src="user.image"
                                    height="25vh"
                                    contain
                                >
                                </v-img>
                            </v-flex>

                        </v-layout>
                    </v-card>
                </v-flex>
            </v-layout>
        </v-container>
    </v-content>
</template>

<script>
export default {
    name: 'dashboard',
    data(){
        return{
            hello: "HELLO WORLD",
            user: {
                id: 1,
                email: "darlan.vieira",
                name: "darlan",
                ca: "2018",
                image: "https://randomuser.me/api/portraits/men/32.jpg"
            }
        }
    },
    
}
</script>
