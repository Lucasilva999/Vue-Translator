<template>
    <p class="h6">{{ translatedText }}</p>
</template>

<script>
export default {
    name: 'translateOutput',
    props: ['translatedText']
}
</script>