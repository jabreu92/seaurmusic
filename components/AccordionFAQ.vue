<template>
  <div>
    <div :key="index" v-for="(item,index) in details" role="tablist">
      <b-card no-body class="mb-1">
        <b-card-header header-tag="header" class="p-1" role="tab">
          <b-button
            block
            href="#"
            v-b-toggle="'accordion-' + index"
            variant="yellow"
            >{{item.title}}</b-button
          >
        </b-card-header>
        <b-collapse
          :id="'accordion-' + index"
          accordion="my-accordion"
          role="tabpanel"
        >
          <b-card-body>
            <b-card-text>{{ item.content }}</b-card-text>
          </b-card-body>
        </b-collapse>
      </b-card>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      details:[
              {
                  title: 'Who Made This Web App ?',
                  content: 'TBD'
              },
              {
                  title: 'More About The Author',
                  content: 'TBD'
              },
              {
                  title: 'Career Experience ',
                  content: 'TBD'
              },
              {
                  title: 'Hobbies',
                  content: 'TBD'
              },
              {
                  title: 'Author Roots',
                  content: 'TBD'
              },
              {
                  title: 'Contact Info',
                  content: 'TBD'
              },
              {
                  title: 'UW Info',
                  content: 'TBD'
              },
              {
                  title: 'Current Life',
                  content: 'TBD'
              }
          ]
    }

  }
}
</script>
