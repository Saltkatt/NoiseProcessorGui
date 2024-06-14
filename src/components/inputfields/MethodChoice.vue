<template>
    <div>
        <label>Methods:</label>
        <select v-model="method">
            <option value="gaussian">Gaussian</option>
            <option value="saltpepper">Salt & Pepper</option>
            <option value="grayscale">Gray</option>
            <option value="blurr">Blurr</option>
            <option value="movingblurr">Moving Blurr</option>
            <option value="obstruction">Obstruction (Rectangle)</option>
        </select>
    </div>
    <div class="grid-container">
    <div v-if="method === 'gaussian'">
        <label>Sigma Value:</label>
        <input type="sigma" v-model="sigma">
    </div>
    <div v-if="method === 'saltpepper'">
        <label>Salt Probability (0-1):</label>
        <input type="salt" v-model="salt">
    </div>
    <div v-if="method === 'saltpepper'">
        <label>Pepper Probability (0-1):</label>
        <input type="pepper" v-model="pepper">
    </div>
    <div v-if="method === 'shape'">
        <label>Rectangle Height (0-240):</label>
        <input type="height" v-model="height">
    </div>
    <div v-if="method === 'shape'">
        <label>Rectangle Width (0-320):</label>
        <input type="width" v-model="width">
    </div>
    <div v-if="method === 'shape'">
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
    <div v-if="method === 'shape'">
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
</template>

<script>
export default {
    emits: ['update-method'],
    data() {
        return {
            method: 'gaussian',
            sigma: 25,
            salt: 0.01,
            pepper: 0.01,
            height: 100,
            width: 50,
            colour: 'green',
            placement: 'center'
        }
    },
    methods: {
        emitMethod() {
            let parameters = {};
            switch (this.method) {
                case 'gaussian':
                    parameters.sigma = this.sigma;
                    break;
                case 'saltpepper':
                    parameters.salt = this.salt;
                    parameters.pepper = this.pepper;
                    break;
                case 'shape':
                    parameters = {
                        height: this.height,
                        width: this.width,
                        colour: this.colour,
                        placement: this.placement
                    };
                    break;
                default:
                    break;
            }
            this.$emit('update-method', {
                method: this.method,
                parameters: parameters
            });
        }
    },
    watch: {
        method() {
            this.emitMethod();
        },
        sigma() {
            if (this.method === 'gaussian') {
                this.emitMethod();
            }
        },
        salt() {
            if (this.method === 'saltpepper') {
                this.emitMethod();
            }
        },
        pepper() {
            if (this.method === 'saltpepper') {
                this.emitMethod();
            }
        },
        height() {
            if (this.method === 'shape') {
                this.emitMethod();
            }
        },
        width() {
            if (this.method === 'shape') {
                this.emitMethod();
            }
        },
        colour() {
            if (this.method === 'shape') {
                this.emitMethod();
            }
        },
        placement() {
            if (this.method === 'shape') {
                this.emitMethod();
            }
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