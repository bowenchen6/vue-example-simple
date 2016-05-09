<template>
  <li>
    <div :class="{bold: isFolder}" @click="toggle" @dblclick="changeType">
      {{model.name}}
      <span v-if="isFolder">[{{open ? '-' : '+'}}]</span>
    </div>
    <ul v-if="isFolder">
      <item class="item" v-for="model in model.children" :model="model"></item>
      <li @click="addChild">+</li>
    </ul>
  </li>
</template>

<script>
import Vue from 'vue';
import Item from './components/Item';

export default {
  components: { Item },
  props: {
    model: Object,
  },
  data() {
    return {
      open: true,
    };
  },
  computed: {
    isFolders() {
      return this.model.children &&
        this.model.children.length;
    },
  },
  methods: {
    toggle() {
      if (this.isFolder) {
        this.open = !this.open;
      }
    },
    changeType() {
      if (!this.isFolder) {
        Vue.set(this.model, 'children', []);
        this.addChild();
        this.open = true;
      }
    },
    addChild() {
      this.model.children.push({
        name: 'new stuff',
      });
    },
  },
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.item {
  cursor: pointer;
}
.bold {
  font-weight: bold;
}
ul {
  padding-left: 1em;
  line-height: 1.5em;
  list-style-type: dot;
}
</style>
