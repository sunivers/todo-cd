<template>
  <div>
    <button v-on:click="clearAllItems">clear all</button>
  </div>
</template>

<script>
export default {
	methods: {
		clearAllItems: function() {
			this.$emit('clear');
		},
	},
};
</script>

<style>
</style>
