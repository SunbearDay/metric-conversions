<script setup lang="ts">
function convertFahrenheitToCelsius(fahrenheit: number): number {
  return (5 / 9) * (fahrenheit - 32)
}

function convertCelsiusToFahrenheit(celsius: number): number {
  return ((celsius * 1.8) + 32)
}

function updateCelsiusInput(event: Event) {
  let elCelsius = document.querySelector('#celsius') as HTMLInputElement
  let celsius = convertFahrenheitToCelsius((event.target as HTMLInputElement).valueAsNumber)
  elCelsius.value = formatConversion(celsius)
}

function updateFahrenheitInput(event: Event) {
  let elFahrenheit = document.querySelector('#fahrenheit') as HTMLInputElement
  let fahrenheit = convertCelsiusToFahrenheit((event.target as HTMLInputElement).valueAsNumber)
  elFahrenheit.value = formatConversion(fahrenheit)
}

function formatConversion(value: number): string {
  let output = value.toFixed(1).toString().split('.')
  if (output.length > 1 && output[1] === "0") return output[0]
  return output.join('.')
}
</script>

<template>
  <div class="container">
    <h2>Temperature Conversions</h2>

    <article class="conversion-input">
      <div>
        <label for="fahrenheit">Fahrenheit</label>
        <input type="number" name="fahrenheit" id="fahrenheit" step="0.1"
          @input="updateCelsiusInput($event)">
      </div>
      <div>
        <label for="celsius">Celsius</label>
        <input type="number" name="celsius" id="celsius" step="0.1"
          @input="updateFahrenheitInput($event)">
      </div>
    </article>

    <article class="info">
      <p>A quick, but not so accurate way to convert fahrenheit to celsius is to subtract 30 from the fahrenheit temperature and then divide by two.</p>
    </article>

    <article class="info">
      <p>Here's two formulas to calculate fahrenheit to celsius:</p>
      <p>C = (5 / 9) x (F - 32)</p>
      <p>C = (F - 32) / 1.8</p>
    </article>

    <article class="info">
      <p>Here's the formula to calculate celsius to fahrenheit:</p>
      <p>F = (C x 1.8) + 32</p>
    </article>
  </div>
</template>

<style scoped>
.container {
  margin-block: 1rem;
}

.conversion-input {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
  justify-content: center;
  margin-bottom: 1rem;
  padding-block: 1em;
}

.conversion-input > div {
  display: grid;
  gap: 0.3em;
  text-align: center;
}

input {
  max-width: 10ch;
}

input[type=number] {
  -moz-appearance: textfield;
}
.info {
  margin-bottom: 1rem;
}
</style>