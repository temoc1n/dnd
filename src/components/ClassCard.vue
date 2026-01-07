<template>
<div class="card rounded-5 mb-3 p-3 d-flex flex-column justify-content-center align-items-center" :style="{ backgroundImage: `url(${backgroundImage()})` }" v-on:click="show = !show">
    <div v-if="show" class="details">
        <h4 class="mb-2">{{ className }}</h4>
        <p class="mb-3 description">{{ classData.Description }}</p>
        <ul class="list-unstyled mb-0">
            <li><strong>Primary Ability:</strong> {{ classData['Primary Ability'] }}</li>
            <li><strong>Scales:</strong> {{ formatList(classData.Scales) }}</li>
            <li><strong>Armor:</strong> {{ formatList(classData.Armor) }}</li>
            <li><strong>Weapons:</strong> {{ formatList(classData.Weapons) }}</li>
            <li><strong>Skills:</strong> {{ formatList(classData.Skills) }}</li>
        </ul>
    </div>
    <div v-else>
        <h1>{{ className }}</h1>
    </div>
</div>
</template>

<script>
export default {
  name: 'ClassCard',
  props: {
    classHero: {
      type: Object,
      required: true
    }
  },
  data(){
    return {
        image_path: "@/assets/images/",
        show: false
    }
  },
  computed: {
    className() {
      return Object.keys(this.classHero)[0];
    },
    classData() {
      return this.classHero[this.className];
    }
  },
  methods: {
    formatList(value) {
      if (Array.isArray(value)) {
        return value.join(', ');
      }
      return value; // string or undefined
    },
    backgroundImage(){
        return require(`@/assets/images/${this.className.toLowerCase()}.jpg`);
    }
  }
}
</script>
<style scoped>
.card {
    color: white !important;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8);
    background-size: cover;
    background-position: center;
    /*
Source - https://stackoverflow.com/a
Posted by Ric Flair
Retrieved 2026-01-07, License - CC BY-SA 4.0
*/

    image-rendering: crisp-edges;
    image-rendering: -moz-crisp-edges;          /* Firefox */
    image-rendering: -o-crisp-edges;            /* Opera */
    image-rendering: -webkit-optimize-contrast; /* Webkit (non-standard naming)*/
    -ms-interpolation-mode: nearest-neighbor;   /* IE (non-standard property) */


}

.description {
    color: #ffffffd0 !important;
}
</style>
