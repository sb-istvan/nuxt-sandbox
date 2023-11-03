<template>
    <h1>Nuxt Playground</h1>
    <p>Learning Vue.js and Nuxt by creating small example pages.</p>
    <ul>
        <li><a href="todo">The Classic Todo List</a></li>
        <li><a href="essentials">Essentials from Vue.js Guide page</a></li>
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
input {
    font-family: inherit;
    font-size: inherit;
    padding-inline: .25rem;
}

input {
    margin-right: .25rem;
}
</style>