<template>
  <v-flex xs12 sm6 lg4>
    <v-card height="100%">
      <v-img :height="size ? size : '400px'" :src="member.img || '/images/fox-placeholder.jpg'" class="grey lighten-2">
        <v-layout slot="placeholder" fill-height align-center justify-center ma-0>
          <v-progress-circular indeterminate color="grey darken-5"></v-progress-circular>
        </v-layout>
      </v-img>
      <v-card-title justify-center>
        <h3 class="d-block text-xs-center">{{member.name}}</h3>
        <h4 v-if="memberType !== 'chapterLeader'" class="d-block text-xs-center">{{member.title}}</h4>
        <a
          class="text-xs-center"
          v-if="member.twitter"
          :href="'http://www.twitter.com/' + member.twitter"
        >
          <i class="fab fa-twitter"></i>
          @{{member.twitter}}
        </a>
        <a class="text-xs-center" v-if="memberType !== 'chapterLeader' && member.website.url" :href="member.website.url">
          <i class="fas fa-link"></i>
          {{member.website.url}}
        </a>
        <p v-if="memberType !== 'chapterLeader'" class="text-xs-center">{{member.bio}}</p>
      </v-card-title>
    </v-card>
  </v-flex>
</template>

<script>
export default {
  props: {
    member: {
      type: Object,
      required: true
    },
    memberType: {
      type: String
    },
    size: {
      type: String
    }
  }
};
</script>

<style scoped>
h3,
h4 {
  width: 100%;
  padding-bottom: 10px;
}
p {
  font-size: 16px;
}
a {
  width: 100%;
  font-size: 16px;
  text-decoration: none;
  padding-bottom: 10px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>


