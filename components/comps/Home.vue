<script setup>
defineProps({ message: String })
</script>

<template>
    <h1>Home - {{ message }}</h1>
    <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum iaculis eu felis et eleifend. Integer elit quam,
        sodales ac erat sed, imperdiet vestibulum velit. Cras finibus aliquet ipsum, id tristique lacus imperdiet at. Proin
        mollis aliquet libero id semper. Duis ut erat turpis. Quisque semper magna vitae rutrum efficitur. Aliquam semper
        augue magna, vel dictum est commodo eget. In at lorem nunc. Vivamus hendrerit fermentum dui vel tempor. Pellentesque
        habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Pellentesque euismod lobortis
        suscipit.
    </p>
</template>