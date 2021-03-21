<template>
  <div>
    <b-container fluid>
      <div v-if="!this.loading">
        <b-row>
          <b-col md="3" v-for="event in hiphoprapevents" :key="event.id">
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
            hiphoprapevents: []
        }
    },
     mounted () {
    //let genre = this.$route.params.classificationId
    let genre = 'KnvZfZ7vAv1'
    let url = `https://app.ticketmaster.com/discovery/v2/events?apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw&source=ticketmaster&locale=*&countryCode=US&stateCode=WA&classificationName=music&classificationId=${genre}`

     axios
        .get(url)
        .then(response => {
            this.items = response.data
            this.hiphoprapevents = this.items._embedded.events

               for (let i =0; i<this.hiphoprapevents.length; i++){

                let event_image_array = this.hiphoprapevents[i].images

                let filteredImagesArray = event_image_array.filter(function (el) {
                            return el.width == 640 && el.height == 360;
                 });
                this.hiphoprapevents[i].images = filteredImagesArray
            }
            console.log(this.hiphoprapevents)
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
