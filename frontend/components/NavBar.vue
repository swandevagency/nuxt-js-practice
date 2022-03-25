<template>
    <div>
        <nav>
            <ul>
                <li>
                    <nuxt-link to="/">home</nuxt-link>
                </li>
            </ul>
            <ul>
                <li>
                    <nuxt-link to="/login">login</nuxt-link>
                </li>
            </ul>
            <ul>
                <li>
                    <nuxt-link to="/register">register</nuxt-link>
                </li>
            </ul>
            <ul>
                <li>
                    <nuxt-link to="/protectedRoute">protectedRoute</nuxt-link>
                </li>
            </ul>
        </nav>
    </div>
</template>

<script>
export default {

}
</script>

<style>

</style>