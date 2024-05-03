<template>
  <v-card class="mx-auto d-flex custom-card" width="100%">
    <v-img
      class="align-end text-white"
      height="300"
      max-width="400"
      :src="imgPath(foodItem.name)"
      cover
    ></v-img>
    <div class="custom-content">
      <v-card-title class="custom-title">{{ foodItem.name }}</v-card-title>
      <v-card-subtitle class="custom-subtitle"
        >Category: {{ foodItem.category }}</v-card-subtitle
      >

      <v-card-actions style="justify-content: space-between">
        <v-btn color="orange" @click="exploreClicked" text="Go Back"></v-btn>
        <v-btn color="orange" @click="bookmark(foodItem)">Bookmark</v-btn>
      </v-card-actions>
    </div>
  </v-card>
  <v-timeline align="start">
    <v-timeline-item fill-dot icon="mdi-star" dot-color="red-lighten-2">
      <v-card>
        <v-card-title :class="['text-h6', 'bg-red-lighten-2']">
          nutrition
        </v-card-title>
        <v-card-text class="bg-white text--primary">
          <v-row>
            <ul class="ml-5">
              <li v-for="(value, key) in foodItem.nutritions" :key="key">
                {{ key }}: {{ value }}
              </li>
            </ul>
          </v-row>
        </v-card-text>
      </v-card>
    </v-timeline-item>
    <v-timeline-item fill-dot icon="mdi-star" dot-color="purple-lighten-2">
      <v-card>
        <v-card-title :class="['text-h6', 'bg-purple-lighten-2']">
          Health Benefits
        </v-card-title>
        <v-card-text class="bg-white text--primary">
          <ul>
            <li v-for="(item, index) in foodItem.health_benefits" :key="index">
              {{ item }}
            </li>
          </ul>
        </v-card-text>
      </v-card>
    </v-timeline-item>
    <v-timeline-item fill-dot icon="mdi-star" dot-color="green-lighten-2">
      <v-card>
        <v-card-title :class="['text-h6', 'bg-green-lighten-2']">
          Fun Facts
        </v-card-title>
        <v-card-text class="bg-white text--primary">
          <ul>
            <li
              v-for="(item, index) in foodItem.fun_facts_and_trivia"
              :key="index"
            >
              {{ item }}
            </li>
          </ul>
        </v-card-text>
      </v-card>
    </v-timeline-item>
    <v-timeline-item fill-dot icon="mdi-star" dot-color="indigo-lighten-2">
      <v-card>
        <v-card-title :class="['text-h6', 'bg-indigo-lighten-2']">
          Recipe ideas - 1
        </v-card-title>
        <v-card-text class="bg-white text--primary">
          <ul>
            <li>
              Item Name : {{ foodItem.recipes_and_serving_ideas[0].name }}
            </li>
            <li>ingredients :</li>
            <ul>
              <li
                v-for="(ingredient, index) in foodItem
                  .recipes_and_serving_ideas[0].ingredients"
                :key="index"
              >
                {{ ingredient }}
              </li>
            </ul>
            <li>instructions :</li>
            <ul>
              <li
                v-for="(instruction, index) in foodItem
                  .recipes_and_serving_ideas[0].instructions"
                :key="index"
              >
                {{ instruction }}
              </li>
            </ul>
          </ul>
        </v-card-text>
      </v-card>
    </v-timeline-item>
    <v-timeline-item fill-dot icon="mdi-star" dot-color="purple-lighten-2">
      <v-card>
        <v-card-title :class="['text-h6', 'bg-purple-lighten-2']">
          Recipe ideas - 2
        </v-card-title>
        <v-card-text class="bg-white text--primary">
          <ul>
            <li>
              Item Name : {{ foodItem.recipes_and_serving_ideas[1].name }}
            </li>
            <li>ingredients :</li>
            <ul>
              <li
                v-for="(ingredient, index) in foodItem
                  .recipes_and_serving_ideas[1].ingredients"
                :key="index"
              >
                {{ ingredient }}
              </li>
            </ul>
            <li>instructions :</li>
            <ul>
              <li
                v-for="(instruction, index) in foodItem
                  .recipes_and_serving_ideas[1].instructions"
                :key="index"
              >
                {{ instruction }}
              </li>
            </ul>
          </ul>
        </v-card-text>
      </v-card>
    </v-timeline-item>
    <v-timeline-item fill-dot icon="mdi-star" dot-color="yellow-lighten-2">
      <v-card>
        <v-card-title :class="['text-h6', 'bg-yellow-lighten-2']">
          varieties
        </v-card-title>
        <v-card-text class="bg-white text--primary">
          <ul>
            <li v-for="(varietie, index) in foodItem.varieties" :key="index">
              {{ varietie }}
            </li>
          </ul>
        </v-card-text>
      </v-card>
    </v-timeline-item>
    <v-timeline-item fill-dot icon="mdi-star" dot-color="red-lighten-2">
      <v-card>
        <v-card-title :class="['text-h6', 'bg-red-lighten-2']">
          culinary uses
        </v-card-title>
        <v-card-text class="bg-white text--primary">
          <ul>
            <li v-for="(use, index) in foodItem.culinary_uses" :key="index">
              {{ use }}
            </li>
          </ul>
        </v-card-text>
      </v-card>
    </v-timeline-item>
  </v-timeline>
</template>

<script>
export default {
  props: {
    foodItem: {
      type: Object,
      require: true,
    },
  },
  methods: {
    exploreClicked() {
      this.$emit("explore");
    },
    bookmark(foodItem) {
      const userId = this.$store.state.userModule.user._id;
      const foodId = foodItem._id;
      this.$store.dispatch("bookmarkItem", {
        userId,
        itemId: foodId,
        itemType: "nutrition",
      });
    },
    imgPath(foodItemName) {
      const imgPath = `../../../assets/img/foodItem/${foodItemName}.jpg`;
      return imgPath;
    },
  },
};
</script>

<style>
.custom-content {
  padding: 16px;
}

.custom-title {
  font-size: 24px;
  color: #333; /* Custom color */
}

.custom-subtitle {
  font-size: 18px;
  color: #666; /* Custom color */
}

.custom-text {
  padding: 16px;
  font-size: 16px;
  color: #444; /* Custom color */
}
</style>