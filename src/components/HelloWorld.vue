<template>
  <v-container class="container">
    <v-row>
      <v-col cols="4" offset="4">
        <div class="family empty"></div>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="4" class="pr-0">
        <SingleCard v-if="families.length !== 6" />

        <DoubleCard v-else :items="families.slice(0, 2)" />
      </v-col>

      <v-col cols="4">
        <SingleCard v-if="families.length === 2" />

        <DoubleCard v-else-if="families.length > 2" :items="families.slice(1, 4)" />

        <div v-if="families.length === 1" class="family empty" />

      </v-col>

      <v-col cols="4" class="pl-0">
        <DoubleCard v-if="families.length >= 4" :items="families.slice(3, 6)" />

        <div v-if="families.length <= 3" class="family empty"></div>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="4" offset="4">
        <div class="family empty"></div>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="4" offset="4" class="justify-center d-flex">
          <v-btn @click="updateFamilies('+')" large>+</v-btn>

          <div class="mx-4" />
          <v-btn @click="updateFamilies" large>-</v-btn>
      </v-col>
    </v-row>

    {{families}}
  </v-container>
</template>

<script>
import SingleCard from "@/components/SingleCard.vue";
import DoubleCard from "@/components/DoubleCard.vue";
import { ref } from '@vue/reactivity';

export default {
  components: {
    SingleCard,
    DoubleCard,
  },
  setup() {
    const families = ref(["A", "B"]);

    const updateFamilies = operator => {
      if (operator === "+") {
        if(families.value.length < 6) {
          families.value.push("A");
        }
      } else {
        if(families.value.length > 1) {
          families.value.pop();
        }
      }
    }

    return {
      families,
      updateFamilies
    };
  },
};
</script>

<style scoped>
.container {
  background-color: black;
  height: 100vh;
}

.offset-col {
  background-color: #fff;
}

.family {
  border-radius: 5px;
  height: 200px;
  padding: 10px;
  background-color: rgb(116, 116, 116);
}
.family.double {
  height: 94px;
}
</style>
