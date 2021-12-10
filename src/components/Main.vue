<template>
  <main class="main">
    <div class="main__container">
      <div class="main__picture">
        <img :src="require('@/assets/images/alco.png')" alt="alco">
      </div>
      <div class="main__about-block about">
        <p class="about__title">Информация о пиве</p>
        <Items/>
      </div>
    </div>
  </main>
</template>

<script>
import Items from "./Items";
export default {
  name: "Main",
  components: {
    Items
  }
}
</script>