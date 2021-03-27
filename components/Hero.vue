<template>
  <div>
    <b-container fluid>
      <b-jumbotron bg-variant="info" text-variant="white" class="mb-0 mt-0">
        <template v-slot:header> {{headerText}}</template>
        <template v-slot:lead> {{leadText}}</template>
        <hr class="mb-1" />
        <p>{{addressText}}</p>
        <div>
          <b-button variant="dark" @click="showModal" v-b-modal.modal-1
            >Contact</b-button
          >
          <b-modal
            ref="my-modal"
            id="modal-1"
            hide-footer
            title="SeaUrMusic Info"
          >
            <div class="d-block text-center">
              <div v-if="showContactInfo">
                <p>Email: {{email}}</p>
                <p>Phone: {{phone}}</p>
              </div>
              <b-button variant="info" @click="toggleShowInfo">
                <span v-if="showContactInfo"> Hide Info </span>
                <span v-else> Show Info </span>
              </b-button>
            </div>
            <b-button class="mt-3" variant="dark" block @click="hideModal"
              >Close</b-button
            >
          </b-modal>
        </div>
      </b-jumbotron>
    </b-container>
  </div>
</template>

<script scoped>
export default {
  Name: 'Jumbotron',
  data () {
    return {
      headerText: 'SeaUrMusic',
      leadText: 'Seattle #1 Music Event Provider',
      addressText: 'Located in 1414 Dexter Ave N. Seattle, WA 98109',
      showContactInfo: true,
      email: 'seaurmusic@hotmail.com',
      phone: '787-789-9992'
    }
  },
  methods: {
    showModal (){
      this.$refs['my-modal'].show()
    },
    hideModal() {
       this.$refs['my-modal'].hide()
      },
    toggleShowInfo(){
        this.showContactInfo = !this.showContactInfo
      }
  }

}
</script>

<style scoped></style>
