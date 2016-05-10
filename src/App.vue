<template>
  <div id="app">
    <button id="show-modal" @click="showModal = true">Show Modal</button>
    <!-- use the modal component, pass in the prop -->
    <modal :show.sync="showModal">
      <!--
        you can use custom content here to overwrite
        default content

      <h3 slot="header">custom header</h3>
      <h3 slot="body">custom body</h3>
      <h3 slot="footer">custom footer
        <button class="modal-default-button"
          @click="showModal = false">
          确定
        </button>
      </h3>
      -->
    </modal>
  </div>
  <form id="search">
    Search <input name="query" v-model="searchQuery">
  </form>
  <grid
    :data="gridData"
    :columns="gridColumns"
    :filter-key="searchQuery">
  </grid>
</template>

<script>
import Modal from './components/Modal';
import Grid from './components/Grid';

export default {
  components: {
    Modal,
    Grid,
  },
  data() {
    return {
      showModal: false,
      searchQuery: '',
      gridColumns: ['name', 'power'],
      gridData: [
        { name: 'Chuck Norris', power: Infinity },
        { name: 'Bruce Lee', power: 9000 },
        { name: 'Jackie Chan', power: 7000 },
        { name: 'Jet Li', power: 8000 },
      ],
    };
  },
};
</script>

<style>
body {
  font-family: Menlo, Consolas, monospace;
  color: #444;
}
#app {
  padding-bottom: 50px;
}
</style>
