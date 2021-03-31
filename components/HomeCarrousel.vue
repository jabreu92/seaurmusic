<template>
  <div>
    <h1>{{title}}</h1>
    <section v-if="errored">
      <p>
        We're sorry, we're not able to retrieve this information at the moment,
        please try back later
      </p>
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
          background="dark"
        >
          <b-carousel-slide
            v-for="event in topEvents"
            :key="event.id"
            :img-src="event.images[0].url"
          >
            <div class="d-flex h-100 align-items-center justify-content-center">
              <div>
                <h4 id="caption-head">{{event.name}}</h4>
                <b-button :href="event.url" target="_blank" variant="success"
                  >Click Here to Learn More
                </b-button>
              </div>
            </div>
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
            topEvents: [],
            title: 'Seattle Top 5 Concerts'
        }
    },
    head() {
      return {
        title: this.title,
        meta: [
          // hid is used as unique identifier. Do not use `vmid` for it as it will not work
          {
            hid: 'mainpage-id',
            name: 'description',
            content: 'Main Page'
          }
        ]
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
.carousel-center .carousel-caption {
  top: 20px;
}
#caption-head {
  color: white;
  background-color: grey;
  border-radius: 5px;
}
</style>
