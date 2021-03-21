<template>
  <div>
    <h3>Select your genre</h3>
    <b-row>
      <b-col md="3" v-for="item in items" :key="item.id">
        <b-card
          :title="item.genre"
          :img-src="item.img"
          img-alt="Genre Music"
          img-top
          tag="article"
        >
          <b-card-text>
            {{item.description}}
          </b-card-text>
          <NuxtLink
            :to="{ name: item.name, params: { classificationId: item.classificationId } }"
            class="nav-link"
            ><b-button variant="primary">See Events</b-button></NuxtLink
          >
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
    data() {
        return {
            items: [
                    {
                      id: 1, genre: 'Rock', img:'https://live.staticflickr.com/3895/14374920271_f0818d5cf4_b.jpg',
                      description: '  Lorem ipsum dolor sit amet consectetur  blanditiis minus voluptates molestiae, totam eius.',
                      classificationId: 'KnvZfZ7vAeA',
                      name: 'rockevents'
                    },
                    {
                      id: 2,genre: 'Blues ', img:'https://live.staticflickr.com/5137/5520660917_d1458d5d2a_b.jpg',
                      description: '  Lorem ipsum dolor sit amet consectetur  blanditiis minus voluptates molestiae, totam eius.',
                      classificationId: 'KnvZfZ7vAvd',
                      name: 'bluesevents'
                      },
                    {
                      id: 3,genre: 'Classical ', img:'https://live.staticflickr.com/4135/4778953173_f135e12c8f_b.jpg',
                      description: '  LLorem ipsum dolor sit amet consectetur  blanditiis minus voluptates molestiae, totam eius..',
                      classificationId: 'KnvZfZ7vAeJ',
                      name: 'classicalevents'
                      },
                    {
                      id: 4,genre: 'Pop  ', img:'https://live.staticflickr.com/7260/7444336100_32b3b208c5_b.jpg',
                      description: '  LLorem ipsum dolor sit amet consectetur  blanditiis minus voluptates molestiae, totam eius.',
                      classificationId: 'KnvZfZ7vAev',
                      name: 'popevents'
                      },
                    {
                      id: 5,genre: 'Latin  ', img:'https://live.staticflickr.com/8005/7585087378_bb82fa1670_b.jpg',
                      description: '  LLorem ipsum dolor sit amet consectetur  blanditiis minus voluptates molestiae, totam eius.',
                      classificationId: 'KnvZfZ7vAJ6',
                      name: 'latinoevents'
                    },
                    {
                      id: 6,genre: 'Country ', img:'https://live.staticflickr.com/3253/2721560965_b113d85226_b.jpg',
                      description: '  LoLorem ipsum dolor sit amet consectetur  blanditiis minus voluptates molestiae, totam eius.',
                      classificationId: 'KnvZfZ7vAv6',
                      name: 'countryevents'
                    },
                    {
                      id: 7,genre: 'Hip Hop/ Rap  ', img:'https://live.staticflickr.com/3609/3456262183_96a53f96a2.jpg',
                      description: '  LLorem ipsum dolor sit amet consectetur  blanditiis minus voluptates molestiae, totam eius..',
                      classificationId: 'KnvZfZ7vAv1',
                      name: 'hiphoprapevents'
                      },
                    {
                      id: 8,genre: 'Dance/Electronic ', img:'https://live.staticflickr.com/5714/22280482280_65e76deb9d_b.jpg',
                      description: '  LLorem ipsum dolor sit amet consectetur  blanditiis minus voluptates molestiae, totam eius..',
                      classificationId: 'KnvZfZ7vAvF',
                      name: 'danceelectronicevents'
                      }
            ]
        }
    }
}
</script>

<style></style>
