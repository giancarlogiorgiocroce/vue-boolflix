<template>
    <header>
        <div class="logo">
            <img src="../assets/image/netflix img.jpg" alt="netflix logo">
        </div>
        <div class="searchbar">
            <button>Cerca</button>
            <input type="text" placeholder="Inserisci un titolo da cercare">
        </div>
    </header>
</template>

<script>
export default {

}
</script>

<style scoped lang="scss">
header{
    height: 75px;
    padding: 5px;
    background-color: black;

    display: flex;
    justify-content: space-between;
    align-items: center;

    .logo{
        height: 100%;
        
        img{
            height: 100%;
        }
    }
    button,
    input{
        margin: 0 2rem;
        padding: .2rem;
        border-radius: 7.5px;
    }
    input{
        width: 15vw;
    }
}
</style>