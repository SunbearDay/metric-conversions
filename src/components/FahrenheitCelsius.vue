<script setup lang="ts">
function updateCelsius(event: Event) {
  let target = event.target as HTMLInputElement
  let celsius = document.querySelector('#celsius') as HTMLInputElement
  celsius.value = formatConversion(((target.valueAsNumber - 32) / 1.8))
}

function updateFahrenheit(event: Event) {
  let target = event.target as HTMLInputElement
  let fahrenheit = document.querySelector('#fahrenheit') as HTMLInputElement
  fahrenheit.value = formatConversion(((target.valueAsNumber * 1.8) + 32))
}

function formatConversion(value: number): string {
  let output = value.toFixed(1).toString().split('.')
  if (output.length > 1 && output[1] === "0") return output[0]
  return output.join('.')
}
</script>

<template>
  <div class="container">
    <h2>Fahrenheit to Celsius Conversions</h2>

    <article class="conversion-input">
      <div>
        <label for="fahrenheit">Fahrenheit</label>
        <input type="number" name="fahrenheit" id="fahrenheit" step="0.1"
          @input="updateCelsius($event)">
      </div>
      <div>
        <label for="celsius">Celsius</label>
        <input type="number" name="celsius" id="celsius" step="0.1"
          @input="updateFahrenheit($event)">
      </div>
    </article>
  </div>
</template>

<style scoped>
.container {
  margin-block: 1rem;
}

article {
  padding-block: 1em;
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  justify-content: center;
}

article>div {
  display: grid;
  gap: 0.3em;
  text-align: center;
}
</style>