<template>
  <div>
    <b-container fluid>
      <h1 class="title">{{ title }}</h1>
      <section v-if="errored">
        <p>
          We're sorry, we're not able to retrieve this information at the
          moment, please try back later
        </p>
      </section>
      <section v-else>
        <div v-if="this.loading">
          <p>One Moment... we are getting your request</p>
        </div>
        <div v-else>
          <div v-if="!this.loading">
            <b-row>
              <b-col
                md="3"
                v-for="event in danceelectronicEvents"
                :key="event.id"
              >
                <b-card
                  bg-variant="secondary"
                  text-variant="white"
                  :title="event.name"
                  class="mt-1 mb-1"
                >
                  <BootstrapImage :image-src-url="event.images[0].url" />
                  <b-card-text>
                    Date: {{event.dates.start.localDate}}
                  </b-card-text>
                  <b-card-text>
                    Time: {{event.dates.start.localTime}}</b-card-text
                  >
                  <b-button :href="event.url" target="_blank" variant="success"
                    >Click Here to Learn More
                  </b-button>
                  <template #footer>
                    <small>Last Updated 3min ago</small>
                  </template>
                </b-card>
              </b-col>
            </b-row>
          </div>
        </div>
      </section>
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
            danceelectronicEvents: [],
            title: 'SeaUrMusic Dance Electronic Concerts'
        }
    },
    head() {
      return {
        title: this.title,
        meta: [
          // hid is used as unique identifier. Do not use `vmid` for it as it will not work
          {
            hid: 'danceelectronicevents-id',
            name: 'description',
            content: 'Dance/Electronic Events Page'
          }
        ]
      }
    },
     mounted () {

    let genre = 'KnvZfZ7vAvF'
    let url = `https://app.ticketmaster.com/discovery/v2/events?apikey=QLnzwCGhWDMWq3z894HvbEL1QuKH2XGw&source=ticketmaster&locale=*&countryCode=US&stateCode=WA&classificationName=music&classificationId=${genre}`

     axios
        .get(url)
        .then(response => {
            this.items = response.data
            this.danceelectronicEvents = this.items._embedded.events

               for (let i =0; i<this.danceelectronicEvents.length; i++){
                let event_image_array = this.danceelectronicEvents[i].images
                let filteredImagesArray = event_image_array.filter(function (el) {
                            return el.width == 640 && el.height == 360;
                 });
                this.danceelectronicEvents[i].images = filteredImagesArray
                let date = new Date(this.danceelectronicEvents[i].dates.start.localDate)
                this.danceelectronicEvents[i].dates.start.localDate = date


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

<style></style>
