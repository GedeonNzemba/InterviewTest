<template>
  <div>
    <div class="number" :id="'number-'+number"
                        v-for="number in getRandomNumbers()"
                        @mouseover="didMouseHover(number)"
                        @mouseout="resetNumbers">
      {{ number }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'Numbers',
  props: {
    limit: 0,
  },
  data() {
    return {
      numbers: []
    }
  },
  methods: {
    // Get random numbers from given limit
    getRandomNumbers() {
      let numbers = Array.from({length: this.limit}, (_, i) => i);
      this.shuffleArray(numbers);
      return numbers;
    },
    shuffleArray(array) {
      for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
      }
    },
    // When user hovers over mouse then highlight divided numbers
    didMouseHover(number) {
      const numberElements = document.querySelectorAll('.number');
      for (let i = 0; i < numberElements.length; i++) {
        const num = numberElements[i].textContent.trim();
        if (number % num === 0) {
          numberElements[i].classList.add('active');
        }
      }
    },
    // Reset active numbers class when user leaves number
    resetNumbers() {
      const nums = document.querySelectorAll('.number');
      nums.forEach(num => num.classList.remove('active'))
    }
  }
}
</script>

<style scoped>
.number {
  display: inline-block;
  padding: 5px;
  background-color: lightgrey;
  margin: 5px;
}

.active {
  background-color: red;
}
</style>
