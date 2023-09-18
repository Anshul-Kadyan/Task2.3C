<template>
  <div>
    <!-- Text Interpolation -->
    <h1>{{ greeting }}</h1>

    <!-- Raw HTML [v-html] -->
    <div v-html="rawHTML"></div>

    <!-- Attribute Bindings [v-bind:id] -->
    <button :id="buttonId" @click="changeGreeting">Click Me</button>

    <!-- JavaScript expressions inside syntax i.e. {{ }} -->
    <p>{{ fullMessage }}</p>

    <!-- List Rendering -->
    <ul>
      <!-- v-for with an Array -->
      <li v-for="item in items" :key="item.id">{{ item.text }}</li>
    </ul>

    <!-- Event Handling [v-on:click] -->
    <button @click="incrementCount">Click me to increment: {{ count }}</button>

    <!-- Input Bindings -->
    <input v-model="inputText" placeholder="Type something" />

    <!-- Display the current value of inputText -->
    <p>Input Text: {{ inputText }}</p>

    <!-- v-model modifiers -->
    <input
      :value="trimmedText"
      @input="updateTrimmedText"
      placeholder="Trimmed Input"
    />

    <!-- Display the current value of trimmedText -->
    <p>Trimmed Text: {{ trimmedText }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      greeting: "Anshul Kadyan",
      rawHTML: "<em>Rendered as HTML</em>",
      buttonId: "my-button",
      items: [
        { id: 1, text: "Mango" },
        { id: 2, text: "Watermelon" },
        { id: 3, text: "Pineapple" },
      ],
      count: 0,
      inputText: "",
      trimmedText: "", // Initialize trimmedText
    };
  },
  computed: {
    fullMessage() {
      return `${this.greeting} World`; // Fixed the reference to greeting
    },
  },
  methods: {
    changeGreeting() {
      if (this.greeting === "Anshul Kadyan") {
        // Fixed the condition
        this.greeting = "s223688915";
      } else {
        this.greeting = "Anshul Kadyan";
      }
    },
    incrementCount() {
      this.count++;
    },
    updateTrimmedText(event) {
      this.trimmedText = event.target.value.trim();
    },
  },
};
</script>

<style>
/* Styles for the component */
div {
  font-family: Arial, sans-serif;
  margin: 20px;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

h1 {
  color: #333;
}

button {
  background-color: #007bff;
  color: #fff;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 5px 0;
}

input {
  padding: 5px;
  width: 100%;
  margin: 5px 0;
  border: 1px solid #ccc;
  border-radius: 3px;
}

/* Add more styles as needed for your specific design */
</style>
