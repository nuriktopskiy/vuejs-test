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