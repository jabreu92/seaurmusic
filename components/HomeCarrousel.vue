<template>
  <div>
    <h3>Top 5 Music Events in WA</h3>
      <section v-if="errored">
        <p>We're sorry, we're not able to retrieve this information at the moment, please try back later</p>
          </section>
  <section v-else>
    <div v-if="this.loading"> 
      <p>One Moment... we are getting your request</p>
    </div>
    <div v-else>
      
        <b-carousel
        id="carousel-fade"
        controls
        indicators
        fade
        img-width="1024"
        img-height="683"
        class="mb-1 mt-0"
          >
          <b-carousel-slide
          v-for="event in topEvents"
          :key="event.id"
          :img-src="event.images[0].url"
          :caption="event.name"
        >
        </b-carousel-slide>
  </b-carousel>
    </div>
     </section>
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
        .get('https://app.ticketmaster.com/discovery/v2/events?apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw&locale=*&size=5&countryCode=US&stateCode=WA&classificationName=music')
        .then(response => {
            this.items = response.data
            this.topEvents = this.items._embedded.events
            
            //Filtering images from the events to be only 1024 width && 683 height
            for (let i =0; i<this.topEvents.length; i++){
                let event_image_array = this.topEvents[i].images
                let filteredImagesArray = event_image_array.filter(function (el) {
                            return el.width == 1024 && el.height == 683;
                 });
                this.topEvents[i].images = filteredImagesArray
            }
            
            //If no data is found
           if(this.items.length == 0){
             this.errored = true 
           }
      


        })
        .catch(error => {
            console.log(error)
            this.errored = true
            })
        .finally(() => this.loading = false)

        }
    }
</script>

<style scoped>

.carousel-caption{
    position: relative;
    left: 0;
    top: 0;
    color: red;
 
}

</style>
