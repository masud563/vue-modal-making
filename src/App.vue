<template>
  <h1>{{ title }}</h1>
  <p>welcome...</p>
  <button @click="toggleModal">Open modal One</button> <br>
  <button @click="toggleModalTwo">Open modal Two</button>
  <teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
      <h1>Ninja Giveaway</h1>
      <p>Grab your ninja swag for half price!</p>
    </Modal>  
  </teleport>

  <teleport to=".modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <template v-slot:links>
        <button>Get Weekly Newsletter</button>
      </template>
      <label for="email">Email:</label>
      <input type="email">
    </Modal>
  </teleport>
</template>

<script>

import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {
    Modal
  },
  data() {
    return {
      title: 'My First Vue App :)',
      showModal: false,
      showModalTwo: false,
    }
  },

  methods: {

    toggleModal() {
      this.showModal = !this.showModal
    },

    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }

}
</script>

<style>

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;

}

button {
  margin: 10px;
  padding: 5px;
}
</style>
