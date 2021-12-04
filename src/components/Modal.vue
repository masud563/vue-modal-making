<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{sale : theme === 'sale'} " >
      <slot>default content</slot>
      <div class="actions">
        <slot name="links">fallback content</slot>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: [ 'theme'],

    methods: {
      closeModal() {
        this.$emit('close')
      }
    }
  }
  
</script>
<style>
  .backdrop {
    top: 0;
    position: fixed;
    background-color: rgba(0, 0, 0,0.5);
    width: 100%;
    height: 100%;
  }

  .modal {
    margin: 100px auto;
    background-color: #fff;
    display: inline-block;
    padding: 20px;
    width: 420px;
    border-radius: 10px;
  }

  .modal h1 {
    color:rgb(13, 184, 155);
  }

  .modal p {
    font-style: normal;
  }

  .modal.sale {
    background-color: crimson;
    color: white;

  }

  .modal.sale h1 {
    color: white;
  }

  .modal .actions {
    margin: 10px;
  }

  .modal .actions a {
    text-decoration: none;
    color: white;
    border: 1px solid white;
    border-radius: 4px;
    padding: 10px;
    margin: 10px;
  }
</style>