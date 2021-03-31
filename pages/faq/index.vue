<template>
  <div>
    <b-container fluid>
      <h1 class="title">{{ title }}</h1>
      <AccordionFAQ />
    </b-container>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        title: 'SeaUrMusic FAQ'
      }
    },
    head() {
      return {
        title: this.title,
        meta: [
          // hid is used as unique identifier. Do not use `vmid` for it as it will not work
          {
            hid: 'faq-id',
            name: 'description',
            content: 'FAQ Page'
          }
        ]
      }
    }
  }
</script>

<style></style>
