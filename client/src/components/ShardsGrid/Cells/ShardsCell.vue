<template>
  <v-row align="start" justify="start" no-gutters v-if="index">
    <v-col
      style="flex-grow: 0"
      v-for="(x, i) in index.primaries || []"
      :key="`p-${i}`"
    >
      <shard-square
        :id="x.shard"
        :state="x.state"
        :fromNode="x.fromNode"
        :progress="x.progress"
        :index="indexName"
        :node-name="nodeName"
        primary
      />
    </v-col>
    <v-col
      style="flex-grow: 0"
      v-for="(x, i) in index.replicas || []"
      :key="`r-${i}`"
    >
      <shard-square
        :id="x.shard"
        :state="x.state"
        :fromNode="x.fromNode"
        :progress="x.progress"
        :index="indexName"
        :node-name="nodeName"
      />
    </v-col>
  </v-row>
</template>

<script>
import ShardSquare from "../ShardSquare.vue";
export default {
  props: {
    index: {
      required: true
    },
    nodeName: {
      type: String,
      required: true
    },
    indexName: {
      type: String,
      required: true
    }
  },
  components: { ShardSquare }
};
</script>

<style scoped></style>
