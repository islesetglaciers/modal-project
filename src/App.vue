<template>
  <h1>{{ title }}</h1>
  <p>Welcome!</p>
  <button @click.alt="toggleModal">Open Modal (Alt)</button>
  <teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close-modal="toggleModal">
      <template v-slot:links>
        <a href="#">Sign up NOW!</a>
        <a href="#">More info...</a>
      </template>
      <h1>Ninja Giveaway!</h1>
      <p>Grab your ninja swag for half-price!</p>
    </Modal>
  </teleport>
  <button @click.alt="toggleModal2">Open Modal 2 (Alt)</button>
  <br>
  <!-- Challenge -->
  <teleport to=".modals" v-if="showModal2">
    <Modal @close-modal="toggleModal2">
      <h1>This is a challenge</h1>
      <p>I have succeeded!</p>
    </Modal>
  </teleport>
  <br>
  <input type="text" ref="name">
  <button @click="handleClick">Click Me!</button>  
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
      // header: 'Sign up for the giveaway!',
      // text: 'Grab your ninja swag for half-price!',
      showModal: false,
      showModal2: false
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModal2() {
      this.showModal2 = !this.showModal2
    }
  }
}
</script>

<style>
#app, .modals {
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
