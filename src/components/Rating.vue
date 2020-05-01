<template>
  <div class="rating">
    <ul class="list">
      <li @click="rate(star)" v-for="star in maxStars" :class="{ 'active': star <= stars }" :key="star.stars" class="star">
      <i :class="star <= stars ? 'fas fa-star' : 'far fa-star'"></i> 
      </li>
    </ul>
    
    <div v-if="hasCounter" class="info counter">
      <span class="score-rating">{{ stars }}</span>
      <span class="divider">/</span>
      <span class="score-max">{{ maxStars }}</span>
    </div>

    <div v-if="hasCaption" class="info caption">
      <span class="score-caption">{{ captions[stars] }}</span>
    </div>

    <div v-if="hasEmoji" class="info emoji">
      <span class="score-emoji">
        <i :class="`fas ${emojis[this.stars - 1]}`"></i>
        <span v-if="this.stars < 1">Not rated</span>
      </span>
    </div>


  </div>
</template>

<script>

export default {
  name: 'Rating',
  props: ['grade', 'maxStars', 'hasCounter', 'hasCaption', 'hasEmoji'],
  data() {
    return {
      stars: this.grade,
      captions: ['Not rated', 'Too Bad', 'Bad', 'Normal', 'Good', 'Excellent'],
      emojis: ['fa-frown', 'fa-meh', 'fa-smile']
    }
  },
  methods: {
    rate(star) {
      if (typeof star === 'number' && star <= this.maxStars && star >= 0) {
        this.stars = this.stars === star ? star - 1 : star
      }
      console.log(this.emojis[1])
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import '../styles/rating.scss';
</style>