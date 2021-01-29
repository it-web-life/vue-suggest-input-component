<template>
  <div class="form-input">
    <Input
      class="field"
      type="text"
      name="test"
      :value.sync="inputValue"
      @focus="onFocus"
      @blur="onBlur"
    />
    <Sugggest
      :isFocus="isFocus"
      :suggests="['hogehoge', 'fugafuga', 'hogefugafoo']"
      @clickSuggest="onClickSuggest"
      @mouseover="isHover = true"
      @mouseleave="isHover = false"
    />
  </div>
</template>

<script>
import Input from '@/components/Input.vue';
import Sugggest from '@/components/Sugggest.vue';

export default {
  name: 'SugggestInput',
  components: {
    Input,
    Sugggest
  },
  data: function () {
    return {
      inputValue: '',
      isFocus: false,
      isHover: false,
    }
  },
  methods: {
    onClickSuggest: function (suggestWord) {
      this.inputValue = suggestWord;
      this.isFocus = false;
    },
    onFocus: function () {
      this.isFocus = true;
    },
    onBlur: function () {
      // ホバーしている時のBlurはSuggestをクリックする動作なので、Clickイベントを発生させるため何も処理しない
      if (this.isHover) return;

      this.isFocus = false;
    },
  },
}
</script>

<style scoped>
  .form-input {
    display: inline-block;
    position: relative;
  }
</style>
