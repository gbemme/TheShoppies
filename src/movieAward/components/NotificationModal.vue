<template>
<div>
  <v-dialog
      transition="dialog-top-transition"
      max-width="600"
      height
      hide-overlay
      v-model="display"
  >
      <v-card class="container align-center justify-center">
        <v-card-title>Nominate  Movie</v-card-title>
        <v-card-text>
          <p>You have successfully Nominate </p>
          <h4>Superman</h4>
        </v-card-text>
        <v-card-actions>
          <v-btn
              color="black"
              depressed
              x-large
              class="white--text"
              @click="$emit('remove')"
          >Close</v-btn>
        </v-card-actions>
      </v-card>
  </v-dialog>
</div>
</template>

<script>
export default {
name: "NotificationModal",
  props:{
    display:Boolean
  }
}
</script>

<style scoped>
.container{
  width: 400px;
  height: 400px;
  background: #ffff;
  /*box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.33);*/
  border-radius: 16px;
}

</style>