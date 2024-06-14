<template>
    <form>
        <label>Input folder:</label>
        <input type="text" v-model="inputFolder" placeholder="Enter path to input folder">

        <label>Output folder:</label>
        <input type="text" v-model="outputFolder" placeholder="Enter path to output folder">

        <Method @update-method="handleMethodUpdate"/>
    


        <green-button 
            buttonText="Process"
            @click="processVideo">
        </green-button>


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
            methodDetails: {}
        }
    },
    methods: {
        handleMethodUpdate(data){
            this.methodDetails = data;
            console.log("handleMethods: ", this.methodDetails)
        },
        async processVideo() {
            console.log("Entered processVideo")
            
            try {
                console.log("Method: ", this.methodDetails.method)
                console.log("Parameters: ", this.methodDetails.parameters)
                const result = await eel.process_video(this.inputFolder, this.outputFolder, this.methodDetails.method, this.methodDetails.parameters)();
                console.log('Processing result:', result);
            } catch (error) {
                console.error('Error processing video:', error);
            }
        },
        

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