
<!-- Script -->
<script>
export default {
  data() { // Variables
    return {
        count: 0,
        num: 0,
        num1: 0,
        imageSource: "images/delete-svgrepo-com.svg"
    }
  },
    methods: {
        number(event) { // Operation and caracters
            if (event.target.innerText === 'AC') {
                this.count = 0;
                this.num = 0;
                this.num1 = 0;
            } else if (event.target.tagName === 'IMG') {
                this.count = this.count.slice(0, -1);
                this.num1 = this.num1.slice(0, -1);
            } else if (event.target.innerText === '=') {
                if (this.count.includes("(")) {
                    this.count = eval(this.num ) * eval(this.num1.slice(1))
                } else {
                    this.count = eval(this.count);
                }
            } else if (event.target.innerText === '( )') {
                if (this.count.includes("(")) {
                    this.count += ")"
                } else {
                    this.count += "("
                }
            } else { //Concatenation of numbers
                if (this.count === 0) {
                    this.count = event.target.innerText;
                    this.num = event.target.innerText
                } else if (this.count.includes("(")) {
                   this.count += event.target.innerText
                   this.num1 += event.target.innerText
                } else {
                    this.num += event.target.innerText;
                    this.count += event.target.innerText;
                }
            }
        },
        hoverImage() {// Hover image
            this.imageSource = "./src/images/delete-svgrepo-hover-com.svg"
        },
        resetImage() {
            this.imageSource = "./src/images/delete-svgrepo-com.svg"
        }
    }
  }
</script>

<!-- Template -->
<template>
 <div id="calculator">
  <input type="text" id="display" readonly :value="count">
  <div id="buttons">
    <button @click="number" id="restore">AC</button>
    <button @click="number" class="operator">( )</button>
    <button @click="number" class="operator">%</button>
    <button @click="number" class="operator">/</button>
    <button @click="number" >7</button>
    <button @click="number">8</button>
    <button @click="number">9</button>
    <button @click="number" class="operator">*</button>
    <button @click="number">4</button>
    <button @click="number">5</button>
    <button @click="number">6</button>
    <button @click="number" class="operator">-</button>
    <button @click="number">1</button>
    <button @click="number">2</button>
    <button @click="number">3</button>
    <button @click="number" class="operator">+</button>
    <button @click="number">0</button>
    <button @click="number">.</button>
    <button @click="number" id="delete" @mouseover="hoverImage" @mouseout="resetImage">
    <img :src="imageSource">
    </button>
    <button @click="number" id="equal">=</button>
  </div>
</div>
</template>

<!-- Style -->
<style scoped>

</style>

