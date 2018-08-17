<template>
    <v-app>
        <TopBar/>
        <router-view/>
    </v-app>
</template>

<script>
import TopBar from '@/components/Navigation/Toolbar'
export default {
    name: 'App',
    components: {
        TopBar
    }
}
</script>
