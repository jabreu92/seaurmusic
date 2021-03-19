<template>
  <div>
   <div v-if="!this.loading">
    <b-carousel
      controls
      indicators
      fade
      img-width="1024"
      img-height="683"
      class="mt-1"
    >
      <b-carousel-slide v-for="event in topEvents" :key="event.id" :img-src="event.images[0].url">
        <h1>{{event.name}}</h1>
      </b-carousel-slide>
    </b-carousel>
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
            //Slice array to top 5 elements
            this.topEvents = this.items._embedded.events.slice(0,5)

            //Filtering images from the events to be only 1024 width && 683 height
            for (let i =0; i<this.topEvents.length; i++){

                let event_image_array = this.topEvents[i].images
                
                let filteredImagesArray = event_image_array.filter(function (el) {
                            return el.width == 1024 && el.height == 683;
                 });
                this.topEvents[i].images = filteredImagesArray
            }
            console.log(this.topEvents)
      
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