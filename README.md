# vuejs-test

> Тестовое задание для студии «Банда умников»


## Ознакомление

Проет реализован соблядая все требования, указанные в техническом задании

## Демонстрация кода


### Стандартные файлы
* Содержимое файла `main.js`
    ``` js
    import { createApp } from 'vue'
    import App from './App.vue'
    import './assets/scss/main.scss'
    
    createApp(App).mount('body')
    ```

* Содержимое файла `App.vue`
    ``` vue
    <template>
      <Index />
    </template>
    
    <script>
    import Index from "./components/Index";
    export default {
      name: 'App',
      components: {
        Index
      }
    }
    </script>
    ```

### Созданные компоненты
* `Index.vue`
* `Header.vue`
* `Main.vue`
* `Items.vue`
* `Footer.vue`


* Компонент `Index.vue`
    ``` vue
    <template>
      <Header/>
      <Main/>
      <Footer/>
    </template>
    
    <script>
    import Header from "./Header";
    import Main from "./Main";
    import Footer from "./Footer";
    export default {
      name: "Index",
      components: {
        Header,
        Main,
        Footer
      },
    }
    </script>
    ```

* Компонент `Header.vue`
    ``` vue
    <template>
      <header class="header">
        <span class="header__site-name">Банда алкоголиков</span>
      </header>
    </template>
    
    <script>
    export default {
      name: "Header"
    }
    </script>
    ```

* Компонент `Main.vue`
    ``` vue
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
    ```

* Компонент `Items.vue`
    ``` vue
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
    ```

* Компонент `Footer.vue`
    ``` vue
    <template>
      <footer class="footer">
        <span class="footer__text">Telegram: <a href="tg://resolve?domain=Nurik_178">@nurik_178</a></span>
        <span class="footer__text footer__text--right">Special for «Банда Умников»</span>
      </footer>
    </template>
    
    <script>
    export default {
      name: "Footer"
    }
    </script>
    ```