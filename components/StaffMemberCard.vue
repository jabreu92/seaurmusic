<template>
  <div>
    <b-card
      :title="staff.name.first + staff.name.last"
      :img-src="staff.picture.large"
      img-alt="Genre Music"
      img-top
      tag="article"
    >
      <b-card-text> Email : {{staff.email}} </b-card-text>
      <b-card-text> Phone: {{staff.phone}} </b-card-text>
      <b-card-text> Hometown: {{staff.location.country}} </b-card-text>
      <b-card-text> Age: {{staff.dob.age}} </b-card-text>
    </b-card>
  </div>
</template>

<script>
export default {
 props: {
        staff: {
            type: Object,
            required: true,
            default: null // create a default object if not found ?
        }
    }
}
</script>

<style scoped></style>
