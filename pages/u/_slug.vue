<template>
  <article>
    <h1>{{ mountain.data?.discord_user?.username }}</h1>
    <!-- <MazAvatar
    :src="getAvatar"
    target="_blank"
    no-elevation
    square
    :size="160"
  /> -->
    <h1>{{ getAvatar }}</h1>
    <p v-if="$fetchState.pending">
      <span class="loading"></span>
    </p>
    <p v-else-if="$fetchState.error">Error while fetching mountains 🤬</p>
    <MazBtn href="/"> Go Back </MazBtn>
  </article>
</template>
<script>
import { onMounted } from 'vue';

export default {
  data() {
    return {
      mountain: {},
    };
  },
  async fetch() {
    this.mountain = await this.$http.$get(
      `https://api.lanyard.rest/v1/users/${this.$route.params.slug}` //https://api.lanyard.rest/v1/users/${params.slug}
    );
  },

  async onMounted() {
    await console.log(getAvatar())
  },
  methods: {
    goBack() {
      return this.$router.go(-1);
    },

    getAvatar() {
      return (
        "https://cdn.discordapp.com/avatars/" +
        this.mountain.data?.discord_user?.id +
        "/" +
        this.mountain.data?.discord_user?.avatar +
        ".png?size=4096"
      );
    },
  },
};
</script>
