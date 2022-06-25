<template>
  <div v-if="visible" class="my-4">
    <label :for="name">{{ name }}</label>
    <input
      :id="name"
      class="border border-gray-200 py-2 px-4"
      type="text"
      :name="name"
      :value="value"
      @input="$emit('input', $event.target.value)"
      @change="$emit('change')"
    />
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: 'field',
    },
    value: {
      type: [Number, String],
      default: '',
    },
    visible: {
      type: Boolean,
      default: true,
    },
  },
}
</script>
