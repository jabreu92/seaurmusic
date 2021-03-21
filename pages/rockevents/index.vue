<template>
  <div>
    <b-container fluid>
      <div v-if="!this.loading">
        <b-row>
          <b-col md="3" v-for="event in rockEvents" :key="event.id">
            <b-card
              :title="event.name"
              :img-src="event.images[0].url"
              img-alt="Genre Music"
              img-top
              tag="article"
              class="mt-1"
            >
              <b-card-text> Date: {{event.dates.start.localDate}} </b-card-text>
              <b-card-text> Time: {{event.dates.start.localTime}} </b-card-text>
              <b-card-text>
                Event URL: <a :href="event.url" target="_blank">Click Here</a>
              </b-card-text>
            </b-card>
          </b-col>
        </b-row>
      </div>
    </b-container>
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

    let genre = 'KnvZfZ7vAeA'
    let url = `https://app.ticketmaster.com/discovery/v2/events?apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw&source=ticketmaster&locale=*&countryCode=US&stateCode=WA&classificationName=music&classificationId=${genre}`

     axios
        .get(url)
        .then(response => {
            this.items = response.data
            this.rockEvents = this.items._embedded.events

               for (let i =0; i<this.rockEvents.length; i++){
                let event_image_array = this.rockEvents[i].images
                let filteredImagesArray = event_image_array.filter(function (el) {
                            return el.width == 640 && el.height == 360;
                 });
                this.rockEvents[i].images = filteredImagesArray
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

<style></style>
