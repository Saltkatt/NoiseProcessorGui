<template>
  <button
  :class="{'outline-green': !isHovered && !isClicked, 'light-green': isHovered, 'green': isClicked}"
  @mouseover="isHovered = true"
  @mouseleave="isHovered = false"
  @click="isClicked = !isClicked"
  class="baseButton"
  >{{ buttonText }}</button>
</template>

<script>
export default {
    data() {
        return{
            isHovered: false,
            isClicked: false,
        };
    },
    props: {
            buttonText: {
                type: String,
                default: () => "Label",
            },
    },

};
</script>

<style scoped>
.baseButton {
    margin: 2px;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}
.outline-green {
    background: white;
    color: green;
    border: 1px solid green;
}
.light-green {
    background: rgb(22, 212, 22);
    color: white;
    border: 1px solid rgb(22, 212, 22);
}
.green {
    background: green;
    color: white;
    border: 1px solid green;
}

</style>