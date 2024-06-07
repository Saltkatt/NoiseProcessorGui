<template>
    <form>
        <label>Input folder:</label>
    <input type="input-folder" required v-model="inputFolder">

    <label>Output folder:</label>
    <input type="output-folder" required v-model="outputFolder">

    <Method/>
    


    <green-button 
    buttonText="Process"></green-button>


    </form>
  
</template>

<script>
import Method from "../inputfields/MethodChoice.vue";
import GreenButton from "../buttons/GreenCustomButton.vue";


export default {
    components:{
        Method,
        GreenButton,
     
    },
    data() {
        return {
            inputFolder: '',
            outputFolder: '',
        }
    }

}
</script>

<style>
form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}
label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input, select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}

</style>