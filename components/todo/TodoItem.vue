<script setup>
const props = defineProps(['id', 'done'])
const emits = defineEmits(['remove', 'done'])

</script>

<template>
    <li><input type="checkbox" :id="id" :checked="done" @click="emits('done')">
        <label :for="id" :class="{ done }">
            <slot />
        </label>

        <button class="removebutton" @click="emits('remove', id)">⨯</button>
    </li>
</template>