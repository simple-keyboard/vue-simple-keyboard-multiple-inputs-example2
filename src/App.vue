<template>
  <div id="app">
    <label>First Name</label>
    <input id="firstName" :value="inputs['firstName']" @focus="onInputFocus" @input="onInputChange">
    
    <label>Last Name</label>
    <input id="lastName" :value="inputs['lastName']" @focus="onInputFocus" @input="onInputChange">

    <SimpleKeyboard
      @onChange="onChange"
      @onKeyPress="onKeyPress"
      :input="inputs[inputName]"
      :inputName="inputName"
    />
  </div>
</template>

<script>
import SimpleKeyboard from "./SimpleKeyboard";
import "./App.css";

export default {
  name: "App",
  components: {
    SimpleKeyboard
  },
  data: () => ({
    /**
     * We define the inputs here
     */
    inputs: {
      firstName: "",
      lastName: ""
    },
    inputName: "firstName"
  }),
  methods: {
    onChange(input) {
      this.inputs[this.inputName] = input;
    },
    onKeyPress(button) {
      console.log("button", button);
    },
    onInputChange(input) {
      console.log("Input changed directly:", input.target.id);
      this.inputs[input.target.id] = input.target.value;
    },
    onInputFocus(input) {
      console.log("Focused input:", input.target.id);
      this.inputName = input.target.id;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
