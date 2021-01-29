<template>
  <input
    class="field"
    autocomplete="off"
    :type="type"
    :name="name"
    v-model="inputValue"
    @focus="onFocus"
    @blur="onBlur"
  >
</template>

<script>
export default {
  name: 'Input',
  props: {
    value: {
      type: String,
      default: ''
    },
    type: {
      type: String,
      required: true
    },
    name: {
      type: String,
      default: ''
    },
  },
  computed: {
    inputValue: {	
      get: function() {	
        return this.value;	
      },	
      set: function(value) {	
        this.$emit('update:value', value);
      }	
    }	
  },
  methods: {
    onFocus: function () {
      this.$emit('focus');
    },
    onBlur: function () {
      this.$emit('blur');
    },
  },
}
</script>

<style scoped>
  .field {
    margin-bottom: 0;
    max-width: 100%;
  }
</style>
