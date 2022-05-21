<template>
    <header>
        <div class="logo">
            <img src="../assets/image/netflix img.jpg" alt="netflix logo">
        </div>
        <div class="searchbar" @keyup.enter="findMovieOrSerial()">
            <input v-model="searchInBoolflix" type="text" placeholder="Inserisci un titolo da cercare">
            <button @click="findMovieOrSerial()">Cerca</button>
        </div>
    </header>
</template>

<script>
export default {
    data(){
        return{
            searchInBoolflix: "",
        }
    },
    methods:{
        findMovieOrSerial(){
            console.log(this.searchInBoolflix, 'lato header funziona');
            this.$emit ('findMovieOrSerial', this.searchInBoolflix);
            this.searchInBoolflix = "";
        }
    }
}
</script>

<style scoped lang="scss">
@import '../assets/style/vars';

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
        padding: 5px;
    }
    input{
        width: 15vw;
        border-radius: 7.5px 0 0 7.5px;
    }
    button{
        border-radius: 0 7.5px 7.5px 0;
        background-color: $netflix-red;
    }
}
</style>