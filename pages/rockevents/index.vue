<template>
  <div>
      <h3>Rock events</h3>
  </div>
</template>

<script>
import axios from 'axios'

 export default {
     data() {
        return {
            loading: true,
            items: null,
            errored: false,
            rockEvents: []
        }
    },
     mounted () {
       
   
   
    let genre = this.$route.params.classificationId
    let url = `https://app.ticketmaster.com/discovery/v2/events?apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw&source=ticketmaster&locale=*&countryCode=US&stateCode=WA&classificationName=music&classificationId=${genre}`
    console.log(url)

     axios
        .get(url)
        .then(response => { 
            this.items = response.data
            console.log(this.items) 

      
        })
        .catch(error => {
            console.log(error)
            this.errored = true
            })
        .finally(() => this.loading = false)
            
        }
    }
</script>

<style>

</style>