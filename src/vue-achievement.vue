<template>
  <div
    class="vue-achievement"
    :style="{ 
      backgroundColor, 
      color: textColor, 
      fontFamily: font,
      gridTemplateColumns: `5rem ${achievement.points ? ' 60px' : ' '} auto`
    }"
  >
    <img
      v-if="achievement.img"
      class="achievement-image"
      :src="achievement.img"
    />
    <div v-if="achievement.points" class="achievement-points">
      <div :style="{ backgroundColor: textColor }">
        <h3 :style="{ color: backgroundColor }">{{ achievement.points }}</h3>
      </div>
    </div>
    <div class="achievement-info" :style="{ marginLeft: achievement.points ? '' : '20px' }">
      <span><h3>{{ achievement.title }}</h3></span>
      <span><p>{{ achievement.description }}</p></span>
    </div>
  </div>
</template>

<script lang="ts">
import Vue, { PropType } from 'vue';

interface Achievement {
  id: string
  img: string | undefined
  points: number | undefined
  title: string
  description: string
}

export default /*#__PURE__*/Vue.extend({
  name: 'VueAchievement', // vue component name
  props: {
    achievement: Object as PropType<Achievement>,
    backgroundColor: {
      type: String,
      default: () => "grey"
    },
    textColor: {
      type: String,
      default: () => "white"
    },
    font: {
      type: String,
      default: () => "sans-serif"
    }
  },
  computed: {
  },
  methods: {
  },
});
</script>

<style scoped>
  .vue-achievement {
    display: grid;
    border-radius: 1000px;
    padding: 10px;
  }

  .achievement-image {
    border-radius: 100%;
    width: 100%;
    height: 100%;
    object-fit: cover;
    background-color: lightgrey;
  }

  .achievement-points {
    height: 100%;
    position: relative;
  }

  .achievement-points div {
    position: relative;
    top: 50%;
    left: 50%;
    border-radius: 100%;
    width: 40px;
    height: 40px;
    transform: translate(-50%, -50%);
  }

  .achievement-points div h3 {
    position: absolute;
    margin: 0;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  .achievement-info {
    display: grid;
    height: 5rem;
    grid-template-rows: auto auto;
    width: auto;
  }

  .achievement-info > span {
    position: relative;
  }

  .achievement-info span > h3, p {
    margin: 0;
    position: absolute;
  }

  .achievement-info span > h3 {
    bottom: 0;
  }

  .achievement-info span > p {
    top: 0;
  }
</style>
