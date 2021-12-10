<template>
  <Index />
</template>

<script>
import axios from 'axios';

// axios.get("https://random-data-api.com/api/beer/random_beer")
//     .then((response) => {
//
//     }).catch((err) => {
//   dispatch({type: Actions.FETCH_DATA_ERROR, payload: err})
// })

import Index from "./components/Index";
export default {
  name: 'App',
  components: {
    Index
  }
}
</script>
