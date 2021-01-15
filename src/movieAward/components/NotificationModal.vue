<template>
  <v-row justify="center">
    <v-dialog
        v-model="display"
        persistent
        width="487px"
    >
      <v-card  class="container align-center pa-0">
        <h4 class="font-weight-bold title"> ⚠️</h4>
        <br>
        <h2  class="title font-weight-bold"> Exceeded Nominations</h2>
        <br>
        <v-card-text class="text">You can no longer nominate a movie you had only <br> 5 movie chances and you have exceeded all chances</v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
              color="red"
              outlined
              x-large
              class="mr-3"
              @click="$emit('remove')"
          >
            Cancel
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
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
  background: #FFFFFF;
  /*box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.33);*/
  border-radius: 16px;
  overflow-x: hidden;
}
.title{
  font-size: 30px;
  margin-left: 17px;
}

.text{
  font-weight: normal;
  font-size: 16px;
  margin-left: 5px;
}

</style>