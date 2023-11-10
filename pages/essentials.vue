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

// fourth section
const cars = [
    { model: "Volkswagen", type: "Passat" },
    { model: "Renault", type: "Espace" },
    { model: "Alfa Romeo", type: "Giulietta" }
]

// fifth section
const text = ref("")
const checkedNames = ref([])
const pickedName = ref("")

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
        </section>
        <section id="fifth">
            <h3 style="white-space: pre-line;">Form input bindings {{ text }}</h3>
            <textarea v-model="text" placeholder="Type something" />
            <button @click="console.log($event.target)">OK</button>
            <div>
                <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
                <label for="jack">Jack</label>
            </div>
            <div>
                <input type="checkbox" id="john" value="John" v-model="checkedNames">
                <label for="john">John</label>
            </div>
            <div>
                <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
                <label for="mike">Mike</label>
            </div>
            <div>Picked name: {{ pickedName }}</div>
            <select v-model="pickedName">
                <option disabled value="">Select one name</option>
                <option v-for="name in checkedNames">{{ name }}</option>
            </select>

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