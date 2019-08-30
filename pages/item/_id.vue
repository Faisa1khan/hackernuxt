<template>
  <div class="pa4 code">
    <div class="f2 mb2">
      {{item.title}}
      <template v-if="item.url">
        <a :href="item.url">{{item.url | hostname}}</a>
      </template>
    </div>
    <div class="f3">
      <nuxt-link to="'user/' + item.by">{{item.by}}</nuxt-link>
      <p class="i">{{item.time | timeSince}}</p>
    </div>
    <div class="comment">will show comments here</div>
  </div>
</template>

<script>
import axios from "~/plugins/axios.js";
export default {
  async asyncData({ route }) {
    const response = await axios.get(`item/${route.params.id}.json`);
    return { item: response.data };
  }
};
</script>

<style lang="scss" scoped>
</style>