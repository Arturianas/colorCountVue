<template>

  <p>Array:</p>
  <p>{{ theArray }}</p>
  <p>Colors:</p>
  <div class='colorArrDOM'>
    <color-block
      :key="color"
      :color="color"
      v-for="color in colorArr"
    ></color-block>
  </div>
  <button
    :disabled="btnIsDisabled"
    @click="startCounter"
  >Restart</button>

</template>


<script >
import ColorBlock from './components/ColorBlock.vue'
export default {
  components: {
    ColorBlock
  },


  data() {
    return {
      numbers: {
        One: "red",
        Two: "blue",
        Three: "yellow",
        Four: "green",
        Five: "salmon"
      },
      theArray: [],
      colorArr: [],
      btnIsDisabled: false
    }
  },

  computed: {
    watchArray() {
      return this.theArray.slice();
    },

  },

  watch: {
    watchArray(newVal, oldVal) {
      console.log(newVal)
      this.colorArr = this.theArray.map(item => this.numbers[item]);
    }
  },

  methods: {

    startCounter() {

      this.theArray = [];
      this.btnIsDisabled = true;

      let i = 0;
      const entries = Object.entries(this.numbers);

      const interval = setInterval(() => {
        if (i === entries.length) {
          this.btnIsDisabled = false;
          return clearInterval(interval);
        }

        this.theArray.push(entries[i][0]);


        i++;
      }, 1000);
    }

  },
  
  created() {
    this.startCounter();
  }

}
</script>



<style scoped>
.colorArrDOM {
  display: flex;
  gap: 1rem;
  justify-content: center;
}
</style>
