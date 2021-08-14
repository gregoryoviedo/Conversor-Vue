<template>
    <header class="header-page">{{title}}</header>
</template>
<script>
export default {
    name: 'Header',
    props: {
        title: String
    }
}
</script>
<style scoped>
header {
    text-align: center;
    background: linear-gradient(to right, #5679DE, #19337C);
    color: #eee;
    padding: 1rem;
    font-weight: bold;
    font-size: 2rem;
}
</style>