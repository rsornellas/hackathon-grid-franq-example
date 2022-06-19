<template>
  <div class="red">
    <div v-if="items[0]" class="family double mb-3 d-flex align-end">
      <v-container>
        <v-row>
          <v-col cols="auto" class="pa-0">
            <v-icon>mdi-access-point</v-icon>
          </v-col>

          <v-col cols="auto" class="px-1 py-0">
            <h3>Emprestimo</h3>
          </v-col>

          <v-col cols="12" class="pa-0">
            <h4>Ver mais</h4>
          </v-col>
        </v-row>
      </v-container>
    </div>
    
    <div
      class="family double d-flex align-end"
      :class="items[1] ? '' : 'empty'"
    >
      <v-container v-if="items[1]">
        <v-row>
          <v-col cols="auto" class="pa-0">
            <v-icon>mdi-access-point</v-icon>
          </v-col>

          <v-col cols="auto" class="px-1 py-0">
            <h3>Emprestimo</h3>
          </v-col>

          <v-col cols="12" class="pa-0">
            <h4>Ver mais</h4>
          </v-col>
        </v-row>
      </v-container>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style scoped>
.family {
  border-radius: 5px;
  height: 200px;
  padding: 10px;
  background-color: white;
}
.family.double {
  height: 94px;
}
.family.empty {
  background-color: rgb(116, 116, 116);
}
.red {
  background-color: black;
}
</style>
