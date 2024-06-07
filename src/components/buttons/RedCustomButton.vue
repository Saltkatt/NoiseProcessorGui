<template>
    <button
    :class="{'outline-red': !isHovered && !isClicked, 'light-red': isHovered, 'red': isClicked}"
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
  .outline-red {
      background: white;
      color: rgb(209, 3, 3);
      border: 1px solid rgb(209, 3, 3);
  }
  .light-red {
      background: rgb(253, 33, 33);
      color: white;
      border: 1px solid rgb(253, 33, 33);
  }
  .red {
      background: rgb(209, 3, 3);
      color: white;
      border: 1px solid rgb(209, 3, 3);
  }
  
  </style>