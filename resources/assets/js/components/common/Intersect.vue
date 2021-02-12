<template>
	<component :is="$props.type">
		<slot />
	</component>
</template>

<script>
	export default {
		props: {
			type: {
				type: String,
				default: 'div',
			},

			rootMargin: {
				type: String,
				default: '100px',
			},

			threshold: {
				type: [Array, Number],
				default() {
					return [0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1];
				},
			},

			infinite: Boolean,
		},

		mounted() {
			this.observer = new IntersectionObserver(
				([e]) => {
					if (e.intersectionRatio) {
						this.$emit('intersect');

						if (!this.$props.infinite) {
							this.observer.unobserve(this.$el);
						}
					}
				},
				{
					rootMargin: this.$props.rootMargin,
					threshold: this.$props.threshold,
				},
			);

			this.observer.observe(this.$el);
		},
	};
</script>
