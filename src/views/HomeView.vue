<template>
  <div class="container-fluid">
    <div class="header text-center m-5">
      <h3 class="title" style="letter-spacing: 1px; opacity: 0.7;">Your adventure starts here.</h3>
    </div>
    <div class="text-center">
      <h5 class="subtitle" style="letter-spacing: 1px; opacity: 0.7;">Pick your class:</h5>
    </div>
    <div class="d-flex justify-content-center">
      <div id="carouselExample" class="carousel slide" data-bs-ride="carousel" style="width: 100%; max-width: 600px; height: 600px;">
      <div class="carousel-inner h-100">
        <div :class="['carousel-item h-100', {active: index === 0}]" v-for="(hero_class, index) in heroClasses" :key="index">
        <ClassCard :classHero="hero_class" class="w-100 h-100"/>
        </div>
      </div>
      <button class="carousel-control-prev" type="button" data-bs-target="#carouselExample" data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button class="carousel-control-next" type="button" data-bs-target="#carouselExample" data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
      </div>
    </div>
    <div class="footer text-center m-5">
      <h5 style="text-shadow: 0 0 5px rgba(0,0,0,0.5); opacity: 0.4;" class="fs-5 foot-text">Every hero has a story, what's yours?</h5>
    </div>
  </div>
</template>
<script>
import ClassCard from '@/components/ClassCard.vue';
import { Carousel } from 'bootstrap';

export default {
  name: 'HomeView',
  components: {
    ClassCard
  },

  data(){
    return {
      heroClasses: [
        {"Barbarian": {
          "Description": "A fierce warrior of primitive background who can enter a state of battle rage",
          "Primary Ability": "Strength",
          "Scales": ["Strength", "Constitution"],
          "Armor": ["Light Armor", "Medium Armor", "Shields"],
          "Weapons": ["Simple Weapons", "Martial Weapons"],
          "Skills": ["Animal Handling", "Athletics", "Intimidation", "Nature", "Perception", "Survival"],
          "img": "barbarian.jpg"
        }},
        {"Bard": {
          "Description": "An inspiring magician whose power echoes the music of creation",
          "Primary Ability": "Charisma",
          "Scales": ["Dexterity", "Charisma"],
          "Armor": ["Light Armor"],
          "Weapons": ["Simple Weapons", "Hand Crossbows", "Longswords", "Rapiers", "Shortswords"],
          "Skills": "Choose any three",
          "img": "bard.jpg"
        }},
        {"Cleric": {
          "Description": "A priestly champion who wields divine magic in service of a higher power",
          "Primary Ability": "Wisdom",
          "Scales": ["Wisdom", "Charisma"],
          "Armor": ["Light Armor", "Medium Armor", "Shields"],
          "Weapons": ["Simple Weapons", "Magic Staffs"],
          "Skills": ["History", "Insight", "Medicine", "Persuasion", "Religion"],
          "img": "cleric.jpg"
        }},
        {"Druid": {
          "Description": "A priest of the Old Faith, wielding the powers of nature and adopting animal forms",
          "Primary Ability": "Wisdom",
          "Scales": ["Intelligence", "Wisdom"],
          "Armor": ["Light Armor", "Medium Armor", "Shields (non-metal)"],
          "Weapons": ["Clubs", "Daggers", "Darts", "Javelins", "Maces", "Quarterstaffs", "Scimitars", "Sickles", "Slings", "Spears"],
          "Skills": ["Arcana", "Animal Handling", "Insight", "Medicine", "Nature", "Perception", "Religion", "Survival"],
          "img": "druid.jpg"
        }},
        {"Warrior": {
          "Description": "A master of martial combat, skilled with a variety of weapons and armor",
          "Primary Ability": "Strength or Dexterity",
          "Scales": ["Strength", "Constitution"],
          "Armor": ["All Armor", "Shields"],
          "Weapons": ["Simple Weapons", "Martial Weapons"],
          "Skills": ["Acrobatics", "Animal Handling", "Athletics", "History", "Insight", "Intimidation", "Perception", "Survival"],
          "img": "warrior.jpg"
        }},
        {"Monk": {
          "Description": "A master of martial arts, harnessing the power of the body in pursuit of physical and spiritual perfection",
          "Primary Ability": "Dexterity and Wisdom",
          "Scales": ["Strength", "Dexterity"],
          "Armor": "None",
          "Weapons": ["Simple Weapons", "Shortswords"],
          "Skills": ["Acrobatics", "Athletics", "History", "Insight", "Religion", "Stealth"],
          "img": "monk.jpg"
        }},
        {"Rogue": {
          "Description": "A scoundrel who uses stealth and trickery to overcome obstacles and enemies",
          "Primary Ability": "Dexterity",
          "Scales": ["Dexterity", "Intelligence"],
          "Armor": ["Light Armor"],
          "Weapons": ["Simple Weapons", "Hand Crossbows", "Longswords", "Rapiers", "Shortswords"],
          "Skills": ["Acrobatics", "Athletics", "Deception", "Insight", "Intimidation", "Investigation", "Perception", "Performance", "Persuasion", "Sleight of Hand", "Stealth"],
          "img": "rogue.jpg"
        }},
        {"Sorcerer": {
          "Description": "A spellcaster who draws on inherent magic from a gift or bloodline",
          "Primary Ability": "Charisma",
          "Scales": ["Constitution", "Charisma"],
          "Armor": "None",
          "Weapons": ["Daggers", "Darts", "Slings", "Quarterstaffs", "Light Crossbows"],
          "Skills": ["Arcana", "Deception", "Insight", "Intimidation", "Persuasion", "Religion"],
          "img": "sorcerer.jpg"
        }},
        {"Wizard": {
          "Description": "A scholarly magic-user capable of manipulating the structures of reality",
          "Primary Ability": "Intelligence",
          "Scales": ["Intelligence", "Wisdom"],
          "Armor": "None",
          "Weapons": ["Daggers", "Darts", "Slings", "Quarterstaffs", "Light Crossbows"],
          "Skills": ["Arcana", "History", "Insight", "Investigation", "Medicine", "Religion"],
          "img": "wizard.jpg"
        }},
        {"Archer": {
          "Description": "A master marksman who excels at precision, agility, and battlefield control from a distance",
          "Primary Ability": "Dexterity",
          "Scales": ["Dexterity", "Wisdom"],
          "Armor": "Light",
          "Weapons": ["Shortbows", "Longbows", "Light Crossbows", "Daggers", "Shortswords"],
          "Skills": ["Perception", "Acrobatics", "Stealth", "Survival", "Nature", "Athletics"],
          "img": "archer.jpg"
        }},
        {"Ronin": {
          "Description": "A masterless samurai, wandering the land in search of purpose",
          "Primary Ability": "Strength and Dexterity",
          "Scales": ["Strength", "Dexterity"],
          "Armor": ["Light Armor", "Medium Armor", "Shields"],
          "Weapons": ["Simple Weapons", "Martial Weapons"],
          "Skills": ["Acrobatics", "Animal Handling", "Athletics", "History", "Insight", "Intimidation", "Perception", "Survival"],
          "img": "ronin.jpg"
        }},
        {"Shaman": {
          "Description": "A spiritual leader who channels the power of nature and ancestors",
          "Primary Ability": "Wisdom",
          "Scales": ["Wisdom", "Charisma", "Strenght"],
          "Armor": ["Light Armor", "Medium Armor", "Shields"],
          "Weapons": ["Simple Weapons", "Martial Weapons"],
          "Skills": ["Animal Handling", "Insight", "Medicine", "Nature", "Perception", "Survival"],
          "img": "shaman.jpg"
        }}]
      }
    },
    mounted() {
      const carouselElement = document.getElementById('carouselExample');
      if (carouselElement) {
        new Carousel(carouselElement);
      }
    }
  }
</script>
<style scoped>
  .title {
    color: #ffc800; 
  }

  .subtitle {
    color: #f9d552c6; 
  }
  .foot-text {
    font-style: italic;
    color: rgb(255, 255, 255) !important;
  }
</style>
