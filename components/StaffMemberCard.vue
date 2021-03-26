<template>
  <div>
     <b-card bg-variant="secondary" text-variant="white"  :title="staff.name.first + staff.name.last" class="mt-1 mb-1 ">
      <BootstrapImage :image-src-url="staff.picture.large" /> 
      <b-card-text> Email : {{staff.email}} </b-card-text>
      <b-card-text> Phone: {{staff.phone}} </b-card-text>
      <b-card-text> Hometown: {{staff.location.country}} </b-card-text>
      <b-card-text> Age: {{staff.dob.age}} </b-card-text>
      <template #footer>
        <small >Last Updated 3min ago</small>
      </template>
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
