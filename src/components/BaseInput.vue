<template>
<input
 :value="modelValue"
  @input="$emit('update:modelValue', $event.target.value)"
	class="word"
	placeholder="0"
/>
</template>
<script>
export default {
	name: 'BaseInput',
	props: ['modelValue'],
	emits: ['update:modelValue'],
}
</script>
