<template>
    <div class="header" >
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRnpDDd16-m8fTneCbtEI1TYpDiVqegO11beA&s" alt="">
        <h1>¿Quién es ese Pokémon?</h1>

    </div>
</template>

<script>
    export default {
        name: "HeaderSection",
        props: {

        }
        
    }
</script>

<style scoped>
.header{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding-top: 3rem;
    row-gap: 1rem;
}
</style>