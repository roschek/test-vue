<template>
  <div>
    <div class="card-container">
      <div class="card__item" v-for="item in items" :key="item.id">
        <div class="card__header">
          <p class="card__level">
            {{ item.floor }}
          </p>
          <p class="card__rooms">
            {{ item.rooms }} комната -
          </p>
          <p class="card__meters">
            {{ item.square }}м<sup>2</sup>
          </p>
        </div>
        <div class="image__block">
          <p class="card__id">
            №{{ item.id }}
          </p>
          <img class="card__img" src="../static/plain.jpg">
        </div>
        <p class="card__cost">
          {{ item.price_full }}р.
        </p>
        <p class="cost-for-meeter">
          {{ (item.price_real / item.square).toFixed(2) }} за м<sup>2</sup>
        </p>
        <button class="card__button">
          подробнее
        </button>
      </div>
    </div>

  </div>
</template>

<script>

export default {
  computed: {
    items () {
      return this.$store.getters['cards/getCards']
    }
  },
  beforeMount () {
    this.$store.dispatch('cards/fetchData')
  }
}

</script>

<style scoped>
.card-container {
 position: fixed;
  overflow-y: auto;
  background: #F8F8F8;
  height: 100vh;
  margin: 0 176px;
  padding: 20px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  flex-wrap: wrap;
}

.card__item {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  max-width: 270px;
  border-radius: 10px;
  background: white;
  border: 1px solid #EBEBEB;
  padding: 12px 15px;
  transition: .8s;
  margin: 20px;
}

.card__item:hover {
  box-shadow: 0px 5px 20px rgba(86, 86, 86, 0.25);
}

.card__header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.card__level {
  font-style: normal;
  font-weight: bold;
  font-size: 12px;
  line-height: 28px;
  color: #2C323A;
  opacity: 0.5;
}

.card__rooms {
  font-weight: bold;
  font-size: 12px;
  line-height: 28px;
  color: #2C323A;
}

.card__meters {
  font-style: normal;
  font-weight: bold;
  font-size: 12px;
  line-height: 28px;
  color: #2C323A;
}

.card__id {
  border: 1px solid #EBEBEB;
  padding: 2px 10px;
  border-radius: 0px 5px;
  font-style: normal;
  font-weight: bold;
  font-size: 14px;
  line-height: 28px;
  text-transform: uppercase;
  align-self: center;
  max-width: 58px;
  margin-left: auto;
  margin-right: 0;
  display: block;
}

.image__block {
  border: 1px solid #EBEBEB;
  border-radius: 5px;
}

.card__img {
  padding: 1px 10px 31px 10px;
  width: 100%;
  object-fit: cover;
}

.card__cost {
  font-style: normal;
  font-weight: bold;
  font-size: 20px;
  line-height: 28px;
  color: #2C323A;
  margin-top: 11px;
  margin-right: 0;
  margin-left: auto;
}

.cost-for-meeter {
  font-style: normal;
  font-weight: bold;
  font-size: 12px;
  line-height: 28px;
  color: #2C323A;
  margin-right: 0;
  margin-left: auto;
  opacity: .5;
}

.card__button {
  background: #70D24E;
  border-radius: 2px 2px 5px 5px;
  border: none;
  padding: 7px 78px 5px 88px;
  color: white;
  font-style: normal;
  font-weight: bold;
  font-size: 14px;
  line-height: 28px;
  cursor: pointer;
  transition: .8s;
  opacity: 0;
}

.card__item:hover > .card__button {
  opacity: 1;
}
</style>
