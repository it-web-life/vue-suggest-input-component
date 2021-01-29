<template>
  <div
    v-show="isFocus"
    class="suggest"
    :style="{ width: sugggestWidth + 'px' }"
    @mouseover="$emit('mouseover')"
    @mouseleave="$emit('mouseleave')"
  >
    <ul class="sugggest-list">
      <li
        class="sugggest-item"
        v-for="(suggest, index) in suggests"
        :key="index"
        @click="onClick(suggest)"
      >
        {{ suggest }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Suggest',
  props: {
    isFocus: {
      type: Boolean,
      default: false
    },
    suggests: {
      type: Array,
      default: function () {
        return [];
      }
    },
    sugggestWidth: {
      type: Number,
      default: 300
    }
  },
  methods: {
    onClick: function (suggest) {
      this.$emit('clickSuggest', suggest);
    }
  },
}
</script>

<style scoped>
  .suggest {
    position: absolute;
    top: 100%;
    overflow-y: scroll;
    background-color: #fff;
    margin-top: -1px;
    padding: 5px;
    border: 1px solid #dedede;
  }

  .sugggest-list {
    list-style-type: none;
    margin: 0;
    padding: 0;
    text-align: left;
  }

  .sugggest-item {
    display: block;
  }
</style>
