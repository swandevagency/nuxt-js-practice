<template>
    <div>
        <nav>
            <ul>
                <li>
                    <nuxt-link to="/">home</nuxt-link>
                </li>
                <li>
                    <nuxt-link to="/login">login</nuxt-link>
                </li>
                <li>
                    <nuxt-link to="/register">register</nuxt-link>
                </li>
                <li>
                    <nuxt-link to="/protectedRoute">protectedRoute</nuxt-link>
                </li>
                <li v-if="authenticated">
                    <span @click="logout">logout</span>
                </li>
            </ul>
        </nav>
    </div>
</template>

<script>
export default {
    props: [
        "authenticated"
    ],
    methods: {
        logout(){
            console.log("logout");
        }
    }
}
</script>

<style>

</style>