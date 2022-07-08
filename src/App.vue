<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <!-- by putting the : before header and text, we are "binding" to the data
  We could just have header="Sign up ..." but we moved it to the 
  data function so we bind to it like below 
  -->
  <teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">Sign Up now</a>
        <a href="#">More info</a>
      </template>
      <h1>Ninja Givaway</h1>
      <p>Grab your ninja swag for half price!</p>
    </Modal>
  </teleport>

  <teleport to=".modals" v-if="showModal2">
    <Modal @close="toggleModal2">
      <h1>Free Judo Lessons</h1>
      <p>Take a flying lessing from a judo master!</p>
    </Modal>
  </teleport>
  <button @click="toggleModal">Show Modal</button>
  <button @click="toggleModal2">Show Modal 2</button>
</template>

<script>
import Modal from './components/Modal';

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'My First Vue App :)',
      showModal: false,
      showModal2: false,
    };
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2;
    },
  },
};
</script>

<style>
#app,
.modal {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
