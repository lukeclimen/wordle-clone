<template>
  <div
    class="flex justify-center items-center"
    :class="[
      { 'not-locked': letterState === 'notLocked' },
      { 'correct-position': letterState === 'correctPosition' },
      { 'wrong-position': letterState === 'wrongPosition' },
      { 'not-in-word': letterState === 'notInWord' },
      { default: letterState === 'default' }
    ]"
  >
    <slot></slot>
  </div>
</template>

<script setup>
defineProps({
  letterState: {
    type: String,
    required: false,
    default: 'notLocked',
    validator(value) {
      return [
        'default',
        'notLocked',
        'correctPosition',
        'wrongPosition',
        'notInWord'
      ].includes(value);
    }
  }
});
</script>

<style scoped>
.default,
.not-locked,
.correct-position,
.wrong-position,
.not-in-word {
  width: 100%;
  height: 100%;
}
.not-locked {
  background-color: white;
  transition: all 0s 0.6s;
}

.correct-position {
  background-color: #538d4e;
  transition-property: background-color;
}

.wrong-position {
  background-color: #c9b458;
  transition-property: background-color;
}

.not-in-word {
  background-color: #787c7e;
  transition-property: background-color;
}

.default {
  background-color: #d3d6da;
  transition-property: background-color;
}

.letter-1 > div {
  transition-delay: 0.375s;
}

.letter-2 > div {
  transition-delay: 0.875s;
}

.letter-3 > div {
  transition-delay: 1.375s;
}

.letter-4 > div {
  transition-delay: 1.875s;
}

.letter-5 > div {
  transition-delay: 2.375s;
}
</style>
