<template>
  <div>
    <form class="form-area">
      <div class="form-element"><p>Комнаты</p>
        <div class="form-rooms">
          <button>s</button>
          <button>1k</button>
          <button>2k</button>
          <button>3k</button>
        </div>
      </div>
      <div class="form-element"><p>Этаж</p>
        <div class="form-input-area">
          <p>{{ minFloor }}</p>
          <p>{{ maxFloor }}</p>
        </div>
        <input type="range" min="1" max="99" v-model.number="minFloor" @change="setRangeSlider">
        <input type="range" min="1" max="99" v-model.number="maxFloor" @change="setRangeSlider">
      </div>
      <div class="form-element"><p>Площадь,м<sup>2</sup></p>
        <div class="form-input-area">
          <p>{{ minSquare }}</p>
          <p>{{ maxSquare }}</p>
        </div>
        <input type="range" min="1" max="999" v-model.number="minSquare" @change="setSquare">
        <input type="range" min="1" max="999" v-model.number="maxSquare" @change="setSquare">
      </div>
      <div class="form-element"><p>Стоимость, млн.руб.</p>
        <div class="form-input-area">
          <p>{{ minCost }}</p>
          <p>{{ maxCost }}</p>
        </div>
        <input type="range" min="1" max="99" v-model.number="minCost" @change="setCost">
        <input type="range" min="1" max="99.9" v-model.number="maxCost" @change="setCost">
      </div>
      <div class="form-element">
        <button class="form-button">Применить</button>
        <p class="form-reset">Сбросить фильтр</p>
      </div>
    </form>
  </div>
</template>

<script>
export default {

  computed: {
    items () {
      return this.$store.getters['cards/getCards']
    }
  },
  methods: {
    setRangeSlider () {
      if (this.minFloor > this.maxFloor) {
        let tmp = this.maxFloor
        this.maxFloor = this.minFloor
        this.minFloor = tmp
      }
    },
    setSquare () {
      if (this.minSquare > this.maxSquare) {
        let tmp = this.maxSquare
        this.maxSquare = this.minSquare
        this.minSquare = tmp
      }
    },
    setCost () {
      if (this.minCost > this.maxCost) {
        let tmp = this.maxCost
        this.maxCost = this.minCost
        this.minCost = tmp
      }
    },
  },
  data () {
    return {
      minFloor: 1,
      maxFloor: 99,
      minSquare: 1,
      maxSquare: 999,
      minCost: 1,
      maxCost: 99.9
    }
  }
}

</script>

<style scoped>
.form-button {
  border: none;
  background-color: #70D24E;
  color: white;
  font-style: normal;
  font-weight: bold;
  font-size: 14px;
  padding: 7px 52px 7px 52px;
  cursor: pointer;
  border-radius: 5px;
  outline: none;
}

.form-button:hover {
  background-color: #457e31;
}

.form-reset {
  font-style: normal;
  font-weight: bold;
  font-size: 10px;
  line-height: 28px;
  text-transform: uppercase;
  margin-top: 0;
  color: #2C323A;
  cursor: pointer;
  border-bottom: 1px solid white;
  padding-bottom: 0;
}

.form-reset:hover {
  border-bottom: 1px solid #70D24E;
}

.form-area {
  max-width: 1280px;
  margin: 0 auto 50px auto;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.form-element {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  white-space: nowrap;
  font-style: normal;
  font-weight: bold;
  font-size: 12px;
  line-height: 28px;
  position: relative;
}

.form-element:first-of-type {
  justify-content: start;
}

.form-input-area {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  position: relative;
  box-sizing: border-box;
}

input[type='range'] {
  -webkit-appearance: none;
  position: absolute;
  left: 10px;
  bottom: -10px;
  box-sizing: border-box;
  background-color: transparent;
  width: 90%;
  height: 3px;
  outline: none;
}

input[type='range']::-webkit-slider-thumb {
  -webkit-appearance: none;
  box-sizing: border-box;
  background-color: #70D24E;
  cursor: pointer;
  z-index: 2;
  position: relative;
  width: 14px;
  height: 14px;
  top: 2px;
  margin-top: -7px;
  outline: none;
  border-radius: 50%;
}

input[type='range']::-webkit-slider-runnable-track {
  width: 100%;
  height: 2px;
  outline: none;
  cursor: pointer;
  animate: 0.2s;
  background:gray;
  border-radius: 1px;
  border: none;
  }

.form-input-area p {
  align-self: start;
  width: 80px;
  height: 40px;
  text-align: center;
  border: 1px solid #D8D8D8;
  padding: 8px;
  border-radius: 5px;
  margin: 10px 15px;
}

.form-rooms button {
  margin-top: 10px;
  background: #FFFFFF;
  border: 1px solid #D8D8D8;
  box-sizing: border-box;
  border-radius: 5px;
  font-style: normal;
  font-weight: bold;
  font-size: 16px;
  line-height: 28px;
  cursor: pointer;
  transition: .4s;
}

.form-rooms button:hover {
  background-color: #70D24E;
}
</style>
