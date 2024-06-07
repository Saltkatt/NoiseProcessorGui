<template>
    <div>
        <label>Methods:</label>
        <select v-model="method">
            <option value="gaussian">Gaussian</option>
            <option value="salt&pepper">Salt & Pepper</option>
            <option value="gray">Gray</option>
            <option value="blur">Blur</option>
            <option value="obstruction">Obstruction (Rectangle)</option>
        </select>
    </div>
    <div class="grid-container">
    <div v-if="method === 'gaussian'">
        <label>Sigma Value:</label>
        <input type="sigma" v-model="sigma">
    </div>
    <div v-if="method === 'salt&pepper'">
        <label>Salt Probability (0-1):</label>
        <input type="salt" v-model="salt">
    </div>
    <div v-if="method === 'salt&pepper'">
        <label>Pepper Probability (0-1):</label>
        <input type="pepper" v-model="pepper">
    </div>
    <div v-if="method === 'obstruction'">
        <label>Rectangle Height (0-240):</label>
        <input type="height" v-model="height">
    </div>
    <div v-if="method === 'obstruction'">
        <label>Rectangle Width (0-320):</label>
        <input type="width" v-model="width">
    </div>
    <div v-if="method === 'obstruction'">
        <label>Rectangle Colour:</label>
        <select v-model="colour">
            <option value="red">Red</option>
            <option value="green">Green</option>
            <option value="blue">Blue</option>
            <option value="yellow">Yellow</option>
            <option value="white">White</option>
            <option value="black">Black</option>
        </select>
    </div>
    <div v-if="method === 'obstruction'">
        <label>Rectangle Placement:</label>
        <select v-model="placement">
            <option value="center">Center</option>
            <option value="bottom-left">Bottom Left</option>
            <option value="bottom-right">Bottom Right</option>
            <option value="bottom-center">Bottom Center</option>
            <option value="top-center">Top Center</option>
        </select>
    </div>
</div>
<p>Method chosen: {{ method }}</p>
</template>

<script>
export default {
    data() {
        return {
            method: 'gaussian',
            sigma: '0 -150',
            salt: '0.01',
            pepper: '0.01',
            height: '100',
            width: '50',
            colour: 'green',
            placement: 'center'
        }
    }

}
</script>

<style>
input, select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}

.grid-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: auto auto;
    gap: 10px;
}

.sigma {
    grid-column: 1 / -1;
}

.salt, .pepper {
    grid-column: span 1;
}

</style>