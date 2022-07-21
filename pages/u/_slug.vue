<template>
  <article>
    <MainContent :userName="getUsername" />
    <MazBtn href="/"> Go Back </MazBtn>
  </article>
</template>
<script>
export default {
  data() {
    return {
      userId: "577513401279053864",
      lanyard: {},
    };
  },
  computed: {
    getUsername() {
      return (
        this.lanyard?.data?.discord_user?.username +
          "#" +
          this.lanyard?.data?.discord_user?.discriminator || "Loading..."
      );
    },
    getAvatar() {
      return (
        "https://cdn.discordapp.com/avatars/" +
        this.userId +
        "/" +
        this.lanyard?.data?.discord_user?.avatar +
        ".png"
      );
    },
  },
  async mounted() {
    const lanyard = await this.$lanyard({ userId: this.userId });
    this.lanyard = lanyard;
  },
  components: { MainContent },
};
</script>
