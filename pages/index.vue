<template>
  <div>
    <header>
      <h1 class="title">
        Lorem ipsum dolor sit
      </h1>
      <Filters/>
    </header>
    <main>
      <Cards/>
    </main>
  </div>
</template>

<script>
import Filters from '@/components/Filters'
import Cards from '~/components/Cards'

export default {
  components: {
    Filters,
    Cards
  }
}
</script>
<style scoped>
.title {
  font-size: 32px;
  font-weight: bold;
  text-align: center;
  margin-top: 50px;
}
</style>
