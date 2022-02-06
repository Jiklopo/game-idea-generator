<template>
  <div id="generator">
    <div id="game-ideas">
      <div class="idea-part">
        <h2>Genre</h2>
        <h1>{{ currentGenre }}</h1>
      </div>

      <div class="idea-part">
        <h2>Topic</h2>
        <h1>{{ currentTopic }}</h1>
      </div>

      <div class="idea-part">
        <h2>Mechanic</h2>
        <h1>{{ currentMechanic }}</h1>
      </div>

      <button @click="generateIdea">Generate</button>
    </div>

    <!-- <div class="prevIdeas" v-if="previousIdeasList">
      <h2>Previous ideas</h2>
      <h3 v-for="idea in previousIdeasList" :key="idea.createdOn">
        {{ `${idea.genre} about ${idea.topic} with ${idea.mechanic} mechanic` }}
      </h3>
    </div> -->
  </div>
</template>

<script>
export default {
  name: "GameIdeaGenerator",

  data() {
    return {
      genres: [
        "RPG", "Card Game", "Fighting", "Endless Runner", "Hypercasual",
       "Sandbox", "Real-time Strategy", "Shooter", "RPG", "Puzzle", "Platformer",
       "Survival", "Horror", "Adventure", "Stealth", "Battle Royal",
       "Roguelike", "Life Simulation", "Visual Novel", "Auto Battler",
       "Turn-based Strategy", "Tower Defense", "Racing", 
       "Casino Game", "Simulator"
       ],
      topics: [
        "Wolves", "Space", "Anime", "Cats", "Big Cat", 
        "Primal Ages", "Earthquake", "Catastrophe", 
        "Wind", "Jungles", "Moon", "Lesson", "Class",
        "School", "Computer", "Groups", "Friendship",
        "Coke", "Beverages", "Cooking", "Farming", 
        "Painting", "Colors", "Food", "Water",
        "Swimming Pool", "Knights", "Middle Ages",
        "Furniture", "Circus", "Mathematics", "Any Country",
        "History", "Dogs", "Haunted House", "Empty Apartment",
        "Chocolate", "Photography", "AI", "Industrialization",
        "Concert", "Party", "Light", "Nature", "Traffic Jam",
        "Transport", "Cars", "Boats", "Castles", "Forest", 
        "Desert", "Trees", "Time", "Accident", "Pets",
        "Song", "Music", "Cycling", "Magic", "Missing Pets"
        ],
      mechanics: [
        "Health as a currency", "Detailed Customization", 
        "Bridge Constructing", "Rhythm-based", "Farming",
        "Undo", "Physics Gun", "Chests with random loot",
        "Bullet Control", "Shape Shifting", "Combo",
        "Size Changing", "Dynamic Soundtrack", "Mental Health",
        "Drones", "Allies", "Mini Game for Reloading", "Mini Games",
        "Limited Controls", "Gestures for actions", "Crafting",
        "Coop", "Identity Theft", "Mind Transfer", "Automatization",
        "Character Switching", "Gravity", "Collectibles",
        "Time Control", "Slow Motion", "Destroyable World",
        "Transport", "PvP", "Multiplayer", "Portals", "Daily Quests",
        "Perma-death", "Rewind", "Replay", "Level Builder",
        "Day-Night Cycle", "Grappling Hooks", "Skill Tree",
        "Hill Climbing", "Flying", "Swimming", "Resurrection",
        ],

      currentGenre: "",
      currentTopic: "",
      currentMechanic: "",
      prevIdeas: [],

      textColor: "#533e85",
      highlightColor: "#270d62",
    };
  },

  created() {
    this.generateIdea();
  },

  methods: {
    generateIdea() {
      this.prevIdeas.push({
        genre: this.currentGenre,
        topic: this.currentTopic,
        mechanic: this.currentMechanic,
        createdOn: Date.now(),
      });

      this.currentGenre = getRandomElement(this.genres);
      this.currentTopic = getRandomElement(this.topics);
      this.currentMechanic = getRandomElement(this.mechanics);
    },
  },

  computed: {
    previousIdeasList() {
      const ideas = this.prevIdeas.slice(1);
      return ideas.reverse();
    },
  },
};

function getRandomElement(array) {
  return array[Math.floor(Math.random() * array.length)];
}
</script>

<style scoped>
#game-ideas {
  height: 100vh;

  display: flex;
  flex-direction: column;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
  gap: 1vh;
}

.idea-part h2 {
  font-weight: 100;
  color: v-bind(textColor);
}

.idea-part h1 {
  font-weight: bold;
  color: v-bind(highlightColor);
}

button {
  width: fit-content;
  font-size: 22px;
  background-color: aliceblue;
  color: v-bind(highlightColor);

  border-color: v-bind(highlightColor);
  border-width: 2px;
  border-radius: 10px;

  padding: 10px 20px;
  margin: 20px auto;
  transition-duration: 0.25s;
}

button:hover {
  background-color: v-bind(highlightColor);
  color: aliceblue;
}
</style>