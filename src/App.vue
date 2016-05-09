<template>
  <div id="app">
    <button id="show-modal" @click="showModal = true">Show Modal</button>
    <!-- use the modal component, pass in the prop -->
    <modal :show.sync="showModal">
      <!--
        you can use custom content here to overwrite
        default content
      -->
      <h3 slot="header">custom header</h3>
      <h3 slot="body">custom body</h3>
      <h3 slot="footer">custom footer
        <button class="modal-default-button"
          @click="showModal = false">
          确定
        </button>
      </h3>
    </modal>
  </div>
</template>

<script>
import Modal from './components/Modal';

export default {
  components: { Modal },
  data() {
    return {
      showModal: true,
    };
  },
};
</script>

<style>
body {
  font-family: Menlo, Consolas, monospace;
  color: #444;
}
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
