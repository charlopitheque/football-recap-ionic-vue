<template>
  <ion-page>
    <ion-content>
      {{data}}
    </ion-content>
  </ion-page>
</template>

<script>/* eslint-disable */
  // @ is an alias to /src
  import HelloWorld from '@/components/HelloWorld.vue'
  import axios from 'axios'
  import api from '../api/api'

  export default {
    name: 'home',
    components: {
      HelloWorld
    },
    data () {
      return {
        data: {}
      }
    },
    methods: {
      getData () {
        let config = api.getConfig()
        axios.get("https://apifootball.com/api/?action=get_countries&APIkey=f69353d27af1822a725a19694b57fbe713a8e1197dfa15888366a562bd348df4", config)
          .then(res => {
            console.log(res)
            this.data = res.data;
          })
          .catch(err => {
            console.warn(err)
          })
      }
    },
    mounted () {
      this.getData()
    }
  }
</script>
