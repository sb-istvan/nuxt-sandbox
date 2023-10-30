<script setup>

// first section
const dynamicId = ref("blue")
function switchColor() {
    dynamicId.value === "blue" ? dynamicId.value = "red" : dynamicId.value = "blue"
}

// second section
const isButtonEnabled = ref(true)
const count = ref(0)
const borderBlueDotted = {
    class: "border-blue-dotted",
    id: "second",
}
</script>

<template>
    <nav>
        <a href="/">Back to Nuxt Playground Home</a>
    </nav>
    <h1>Vue Essentials</h1>
    <p>This page is to try out Vue template syntax based on Vue.js Guide.</p>
    <div id="examples">
        <section id="first">
            <p :class="dynamicId">This is either red or blue</p>
            <button @click="switchColor">Switch color</button>
        </section>
        <section v-bind="borderBlueDotted">
            <p>Disable counter button</p>
            <label><input type="checkbox" v-model="isButtonEnabled">
                <button :disabled="!isButtonEnabled" @click="count++">
                    Clicked {{ count }} times
                </button>
            </label>
            <div v-if="count > 3">
                <p>More than 3 clicks!</p>
                <button @click="count = 0">Reset count</button>
            </div>
        </section>
    </div>
</template>

<style>
#examples {
    display: flex;
    gap: .5rem;
}

section {
    display: flex;
    gap: .5rem;
    flex-direction: column;
    border: 2px solid black;
    padding: .5rem;
    border-radius: .5rem;
}

.blue {
    color: darkblue;
    font-weight: bold;
}

.red {
    color: crimson;
    font-weight: bold;
}

.border-blue-dotted {
    border: 2px darkblue dotted;
}
</style>