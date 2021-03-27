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
        staffFullName: {
            type: String,
            required: true,
            default: "John Smith" // Pass in the specific parameters instead of teh whole objet , best practice
        },
        staffPic: {
            type: String,
            required: true,
            default: "https://picsum.photos/200/300" // Pass in the specific parameters instead of teh whole objet , best practice
        },
        staffEmail: {
            type: String,
            required: true,
            default: "Staff Email" // Pass in the specific parameters instead of teh whole objet , best practice
        },
         staffPhone: {
            type: String,
            required: true,
            default: "Staff PhoneNumber" // Pass in the specific parameters instead of teh whole objet , best practice
        },
         staffHometown: {
            type: String,
            required: true,
            default: "Staff Hometown" // Pass in the specific parameters instead of teh whole objet , best practice
        },
         staffAge: {
            type: String,
            required: true,
            default: "Staff Age" // Pass in the specific parameters instead of teh whole objet , best practice
        },



    }
}
</script>

<style scoped></style>
