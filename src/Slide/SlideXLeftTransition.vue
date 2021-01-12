<!-- Accepted transitionConfigCSS:
	{
		'--translateX': '-15px',
	}
-->
<template>
	<component
		:is="componentType"
		:tag="tag"
		v-bind="$attrs"
		v-on="hooks"
		enter-active-class="slideXLeftIn"
		move-class="slide-move"
		leave-active-class="slideXLeftOut"
	>
		<slot></slot>
	</component>
</template>

<script>
import { baseTransition } from '../mixins/baseTransition.js';

export default {
	name: 'slide-x-left-transition',
	mixins: [baseTransition],
	props: {
		styles: {
			type: Object,
			default: () => {
				return {
					'animation-fill-mode': 'both',
					'animation-timing-function': 'cubic-bezier(.25,.8,.50,1)',
				};
			},
		},
	},
};
</script>

<style>
.slide-move {
	transition: transform .3s;
}


@keyframes slideXLeftIn {
	from {
		opacity: 0;
		transform: translateX(var(--translateX, -15px));
	}

	to {
		opacity: 1;
	}
}

.slideXLeftIn {
	animation-name: slideXLeftIn;
}

@keyframes slideXLeftOut {
	from {
		opacity: 1;
	}

	to {
		opacity: 0;
		transform: translateX(var(--translateX, -15px));
	}
}

.slideXLeftOut {
	animation-name: slideXLeftOut;
}
</style>
