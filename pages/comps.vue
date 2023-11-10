<script setup>
import Home from "../components/comps/Home.vue"
import Photos from "../components/comps/Photos.vue"
import Blog from "../components/comps/Blog.vue"
import About from "../components/comps/About.vue"

const currentTab = ref("Home")

const tabs = {
    Home,
    Photos,
    Blog,
    About
}

const message = "Hello Props!"

</script>

<template>
    <nav>
        <a href="/">Back to Nuxt Playground Home</a>
    </nav>
    <div class="buttongroup">
        <button v-for="(_, tab, index) in tabs" :key="tab" @click="currentTab = tab">{{ tab }} ({{ index + 1 }})</button>
    </div>
    <component :is="tabs[currentTab]" :message="message"></component>
</template>

<style>
.buttongroup {
    margin-block: .5rem;
    display: flex;
    gap: .5rem;
}
</style>