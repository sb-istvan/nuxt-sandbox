<script setup>
const pages = [
    {
        route: "todo",
        text: "The Classic Todo List"
    },
    {
        route: "essentials",
        text: "Essentials from Vue.js Guide page"
    },
    {
        route: "comps",
        text: "Practicing components"
    },
]
</script>

<template>
    <h1>Nuxt Playground</h1>
    <p>Learning Vue.js and Nuxt by creating small example pages.</p>
    <ul>
        <li v-for="page in pages"><a :href="page.route">{{ page.text }}</a></li>
    </ul>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Cabin:wght@400;700&display=swap');

* {
    box-sizing: border-box;
    padding: 0rem;
    margin: 0rem;
}

body {
    font-family: 'Cabin', sans-serif;
    padding: .5rem;
}

h1,
p {
    padding-block: .25rem;
}

button,
input,
textarea {
    font-family: inherit;
    font-size: inherit;
    padding-inline: .25rem;
}

input {
    margin-right: .25rem;
}
</style>