<template>
	<nuxt-link :to="$props.url">
		<div class="x-placeholder group overflow-hidden">
			<img
				class="transition-transform duration-200 transform group-hover:scale-105"
				v-bind="$props.img"
			>
		</div>

		<h1
			class="x-h3 x-fade mt-5"
			v-text="$props.title"
		/>
	</nuxt-link>
</template>

<script>
	export default {
		inheritAttrs: false,

		props: {
			title: {
				type: String,
				required: true,
			},

			img: {
				type: Object,
				required: true,
			},

			url: {
				type: String,
				required: true,
			},
		},
	};
</script>
