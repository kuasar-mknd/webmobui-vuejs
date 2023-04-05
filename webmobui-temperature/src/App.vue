<script setup>
import {computed, ref} from 'vue'

const kelvin = ref(0)

const celsius = computed( () => kelvin.value - 273.15)

const fahrenheit = computed( () => kelvin.value * 9 / 5 - 459.67)

function updateKelvin(event) {
  kelvin.value = event.target.value
}

function updateCelsius(event) {
  kelvin.value = calculateKelvinFromCelsius(event.target.value)
}

function updateFahrenheit(event) {
  kelvin.value = calculateKelvinFromFahrenheit(event.target.value)
}

function calculateKelvinFromFahrenheit(input) {
  return Math.round((parseFloat(input) + 459.67) * 5 / 9 * 100) / 100
}

function calculateKelvinFromCelsius(input) {
  return Math.round((parseFloat(input) + 273.15) * 100) / 100
}

</script>

<template>
  <div>
    <label for="kelvin">Kelvin</label>
    <input type="number" id="kelvin" :value="kelvin" @input="updateKelvin($event)">
    <label for="celsius">Celsius</label>
    <input type="number" id="celsius" :value="celsius" @input="updateCelsius($event)">
    <label for="fahrenheit">Fahrenheit</label>
    <input type="number" id="fahrenheit" :value="fahrenheit" @input="updateFahrenheit($event)">
  </div>
</template>

<style scoped>
</style>
