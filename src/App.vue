<template>
<div class="main-div">
  <div>
    <div v-for="i in 4" :key="i">
    <div class="heading" :class="{'selected': initialValue === i}" @click="moveToSelectedStep(i)"><div class="circle">{{ i }}</div> &nbsp; Step {{ i }}</div>
  </div>
  </div>
  <div>
    <component :is="renderComponents[initialValue]" @updateValue="updateValue" :componentsValue="componentsValue"></component>
  <div class="button-section" v-if="initialValue !== 5">
    <button @click="prevComponent" :disabled="disablePrevButton">prev</button>
    <button v-if="showNextButton" @click="nextComponent" :disabled="disableNextButton">next</button>
    <button v-if="initialValue === 4" @click="submitForm">submit</button>
  </div>
  </div>
</div>
</template>

<script>
import TextInput from './inputComponents/TextInput.vue'
import DropDown from './inputComponents/DropDown.vue'
import RadioComponent from './inputComponents/RadioComponent.vue'
import RenderAllInputValues from './inputComponents/RenderAllInputValues.vue'
import FormSubmitted from './inputComponents/FormSubmitted.vue'
export default {
  name: 'App',
  components: {
    TextInput,
    DropDown,
    RadioComponent,
    RenderAllInputValues
  },
  data () {
    return {
      initialValue: 1,
      renderComponents: {
        1: TextInput,
        2: DropDown,
        3: RadioComponent,
        4: RenderAllInputValues,
        5: FormSubmitted
      },
      componentsValue: {
        input: "",
        dropdown: "",
        radio: ""
      },
      inputTypes: ["input", "dropdown", "radio"]
    }
  },
  computed: {
    showNextButton () {
      return this.initialValue <= 3
    },
    disablePrevButton () {
      return this.initialValue === 1
    },
    disableNextButton () {
      for(let i = 1; i<= this.initialValue; i++) {
        if(this.componentsValue[this.inputTypes[i-1]] === "") {
          return true
        }
      }
      return false
    }
  },
  methods: {
    nextComponent () {
      this.initialValue = this.initialValue + 1
    },
    prevComponent () {
      if (this.initialValue === 1) {
        return
      }
      this.initialValue = this.initialValue - 1
    },
    updateValue (val, type) {
      this.componentsValue[type] = val
    },
    submitForm () {
      this.initialValue = 5
    },
    moveToSelectedStep (i) {
      for(let i = 1; i<= this.initialValue; i++) {
        if(this.componentsValue[this.inputTypes[i-1]] === "") {
          return
        }
      }
      this.initialValue = i
    }
  }
}
</script>

<style>
.main-div {
  width: 600px;
  margin: auto;
  /* text-align: center; */
  display: flex;
  justify-content: space-around;
}
.button-section {
  margin-top: 50px;
}
.heading {
  display: flex;
  margin-bottom: 10px;
  cursor: pointer;
}
.circle {
  background-color: skyblue;
  border-radius: 50%;
  height: 20px;
  width: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.selected {
  background: gray;
}
</style>
