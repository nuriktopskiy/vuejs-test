<template>
  <main class="main">
    <div class="main__container">
      <div class="main__picture">
        <img :src="require('@/assets/images/alco.png')" alt="alco">
      </div>
      <div class="main__about-block about">
        <p class="about__title">Информация о пиве</p>
        <ul class="about__list list" :id="res.uid">
          <li class="list__item">Артикул: {{ res.id }}</li>
          <li class="list__item">Бренд: {{ res.brand }}</li>
          <li class="list__item">Название: {{ res.name }}</li>
          <li class="list__item">Стиль: {{ res.style }}</li>
          <li class="list__item">Хмель: {{ res.hop }}</li>
          <li class="list__item">Дрожжи: {{ res.yeast }}</li>
          <li class="list__item">Солод: {{ res.malts }}</li>
          <li class="list__item">IBU: {{ res.ibu }}</li>
          <li class="list__item">Процент алкоголя: {{ res.alcohol }}</li>
          <li class="list__item">Крепкость: {{ res.blg }}</li>
        </ul>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
export default {
  name: "Main",
  data() {
    return {
      res: [],
    }
  },
  methods: {
    async fetchNews() {
      try {
        const url = 'https://random-data-api.com/api/beer/random_beer'
        const response = await axios.get(url)
        this.res = response.data
      } catch (err) {
        if (err.response) {
          // client received an error response (5xx, 4xx)
          console.log("Server Error:", err)
        } else if (err.request) {
          // client never received a response, or request never left
          console.log("Network Error:", err)
        } else {
          console.log("Client Error:", err)
        }
      }
    },
  },
  mounted() {
    this.fetchNews()
  },
}
</script>