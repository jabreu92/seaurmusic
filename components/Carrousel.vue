<template>
  <div>
   <div v-if="!this.loading">
    
   
    
    </div>
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
            topEvents: []
        }
    },
     mounted () {
     axios
        .get('https://app.ticketmaster.com/discovery/v2/events?apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw&locale=*&countryCode=US&stateCode=WA&classificationName=music')
        .then(response => { 
            this.items = response.data
            this.topEvents = this.items._embedded.events.slice(0,5)
            let event_zero = this.topEvents[0]
            let event_zero_images = event_zero.images
            var newArray = event_zero_images.filter(function (el) {
            return el.width == 1024 && el.height == 683;
             });
            console.log(newArray)

            




        })
        .catch(error => {
            console.log(error)
            this.errored = true
            })
        .finally(() => this.loading = false)
            
        }
    }


</script>

<style></style>