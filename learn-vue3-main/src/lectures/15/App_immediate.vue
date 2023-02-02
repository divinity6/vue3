<template>
	<div>
		<p>{{ message }}</p>
		<p>{{ reverseMessage }}</p>
	</div>
</template>

<script>
import { ref, watch } from 'vue';

export default {
	setup() {
		const message = ref('Hello Vue3');
		const reverseMessage = ref('');

		const reverseFunction = () => {
			console.log('즉시실행함!!!');
			reverseMessage.value = message.value.split('').reverse().join('');
		};
    /** 3번째 파라미터로 { immediate : true } 를 넘기면 최초에도 한번 실행함 */
		watch(message, reverseFunction);
		reverseFunction();
		return { message, reverseMessage };
	},
};
</script>

<style lang="scss" scoped></style>
