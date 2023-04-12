<template>
    <header>
        <h1>{{ title }}</h1>
    </header>
</template>

<script>
    export default{
        props: {
            title: String
        }
    }
</script>

<style scoped>
header{
    width: 100%;
    height: 5rem;
    background-color: #640032;
    display: flex;
    justify-content: center;
    align-items: center;
}
h1{
    color: #fff;
    font-size: 2rem;
    text-align: center;
    margin: 0;
}

</style>