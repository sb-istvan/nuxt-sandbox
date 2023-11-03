<script setup>
defineProps(['text', 'done'])
defineEmits(['remove', 'done'])
</script>

<template>
    <li>
        <input type="checkbox" :checked="done" @click="$emit('done')">
        <span :class="{ done }">{{ text }}</span>
        <button class="removebutton" @click="$emit('remove')">⨯</button>
    </li>
</template>