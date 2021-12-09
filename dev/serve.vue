<script lang="ts">
import Vue from 'vue';
import VueAchievement from '@/vue-achievement.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    VueAchievement
  },
  data() {
    return {
      achievement: {
        id: "ABC123",
        img: "https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Fwww.xboxachievements.com%2Fimages%2Fnews%2Fachievements.jpg&f=1&nofb=1",
        points: 150,
        title: "10% weniger Müll",
        description: "Du bist geil",
      }
    }
  }
});
</script>

<template>
  <div id="app">
    <vue-achievement :achievement="achievement" />
  </div>
</template>
