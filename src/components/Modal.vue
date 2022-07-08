<template>
  <div class="backdrop" @click="closeModal">
    <!--
      Even though we have a class="modal" we can add another
      class to data bind to.  This will be a dynamic class
    -->
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <h1>{{ header }}</h1>
      <p>{{ text }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['header', 'text', 'theme'],
  methods: {
    closeModal() {
      this.$emit('close');
    },
  },
};
</script>
<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
/* We add the .modal before the h1 to ensure the styles will only affect
the h1 for this component.  We could also add scoped to the style time 
i.e. <style scoped> but if we do that a lot there is a performance hit. */
.modal h1 {
  color: #03cfb4;
  border: none;
  padding: 0;
}
.modal.sale {
  background: crimson;
  color: white;
}
.modal.sale h1 {
  color: white;
}
</style>
