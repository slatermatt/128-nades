<template>
	<intersect
		type="article"
		@intersect="visible = true"
	>
		<div class="x-placeholder">
			<no-ssr v-if="visible">
				<youtube
					player-width="100%"
					player-height="100%"
					:video-id="$props.video"
				/>
			</no-ssr>
		</div>

		<div class="flex flex-col mt-5 space-y-2 font-light">
			<p>from: <span class="font-bold text-brand-primary" v-text="location.from" /></p>

			<p>to:  <span class="font-bold text-brand-primary" v-text="location.to" /></p>
		</div>
	</intersect>
</template>

<script>
	import Intersect from '../common/Intersect';

	export default {
		components: {
			Intersect,
		},

		props: {
			type: {
				type: String,
				default: "smoke",
			},

			location: {
				type: Object,
				required: true,
			},

			video: {
				type: String,
				required: true,
			},
		},

		data() {
			return {
				visible: false,
			};
		},
	};
</script>
