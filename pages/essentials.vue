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

// third section
const isActive = ref(true)
const hasError = ref(false)
const rectangleClasses = computed(() => ({
    active: isActive.value,
    error: hasError.value,
    combined: isActive.value && hasError.value,
}))

// fouth section
const cars = [
    { model: "Volkswagen", type: "Passat" },
    { model: "Renault", type: "Espace" },
    { model: "Alfa Romeo", type: "Giulietta" }
]

const carObject = {
    model: "Audi",
    type: "A6 Avant",
    color: "white",
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
            <template v-if="count > 9">
                <button @click="count = 0">Reset counter</button>
            </template>
            <template v-else-if="count > 3">
                <p>Continue like this!</p>
            </template>
            <p v-else>Just keep clicking!</p>
        </section>
        <section id="third">
            <div class="rectangle" :class="rectangleClasses"></div>
            <div class="control">
                <h3>Control</h3>
                <label><input type="checkbox" v-model="isActive">active</label>
                <label><input type="checkbox" v-model="hasError">error</label>
            </div>
        </section>
        <section id="fourth">
            <h3>Time for v-for!</h3>
            <ul class="cars">
                <li v-for="({ model, type }, index) in cars">[{{ index }}] {{ model }} {{ type }}</li>
            </ul>
            <ul class="cars">
                <li v-for="(value, key, index) in carObject">{{ index }} - {{ key }} - {{ value }}</li>
            </ul>
        </section>
    </div>
</template>

<style>
#examples {
    display: flex;
    flex-wrap: wrap;
    gap: .5rem;
    padding-block-start: .5rem;
}

section {
    display: flex;
    gap: .5rem;
    flex-direction: column;
    border: 2px solid black;
    padding: .5rem;
    border-radius: .5rem;
    min-width: 12rem;
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

#third {
    display: flex;
    flex-direction: row;
}

.rectangle {
    width: 5rem;
    height: 5rem;
    background-color: lightgrey;
}

.control {
    display: flex;
    flex-direction: column;
}

.active {
    background-color: darkgreen;
}

.error {
    background-color: crimson;
}

.cars {
    padding-left: 1rem;
}
</style>