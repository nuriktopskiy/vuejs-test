<template>
  <ul class="about__list list" :id="res.uid">
    <li class="list__item">
      <span class="list__attribute">Артикул:</span>
      <span class="list__value">{{ res.id }}</span>
    </li>
    <li class="list__item">
      <span class="list__attribute">Бренд:</span>
      <span class="list__value">{{ res.brand }}</span>
    </li>
    <li class="list__item">
      <span class="list__attribute">Название:</span>
      <span class="list__value">{{ res.name }}</span>
    </li>
    <li class="list__item">
      <span class="list__attribute">Стиль:</span>
      <span class="list__value">{{ res.style }}</span>
    </li>
    <li class="list__item">
      <span class="list__attribute">Хмель:</span>
      <span class="list__value">{{ res.hop }}</span>
    </li>
    <li class="list__item">
      <span class="list__attribute">Дрожжи:</span>
      <span class="list__value">{{ res.yeast }}</span>
    </li>
    <li class="list__item">
      <span class="list__attribute">Солод:</span>
      <span class="list__value">{{ res.malts }}</span>
    </li>
    <li class="list__item">
      <span class="list__attribute">IBU:</span>
      <span class="list__value">{{ res.ibu }}</span>
    </li>
    <li class="list__item">
      <span class="list__attribute">Процент алкоголя:</span>
      <span class="list__value">{{ res.alcohol }}</span>
    </li>
    <li class="list__item">
      <span class="list__attribute">Крепкость:</span>
      <span class="list__value">{{ res.blg }}</span>
    </li>
  </ul>
</template>

<script>
import axios from "axios";

export default {
  name: "Items",
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