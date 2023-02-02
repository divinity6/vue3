<template>
	<div></div>
</template>

<script>
import { reactive, ref, watch } from 'vue';

export default {
	setup() {
		const x = ref(0);
		const y = ref(0);

		const obj = reactive({
			count: 0,
		});
    /** 기본적으로 객체형태의 내부 프로퍼티 변경을 확인할 수 있음 */
		// watch(
		// 	() => x.value + y.value,
		// 	(sum, oldValue) => {
		// 		console.log('sum: ', sum);
		// 		console.log('oldValue: ', oldValue);
		// 	},
		// );

		// watch([x, y], ([newX, newY]) => {
		// 	console.log(newX, newY);
		// });
		console.log(typeof obj.count);

    /** getter 로 선언을 해줘야 해당 프로퍼티만! 변경했을때 감지함 */
		// watch(
		// 	() => obj.count,
		// 	(newValue, oldValue) => {
		// 		console.log('newValue: ', newValue);
		// 	},
		// );
		// watch(obj, (newValue, oldValue) => {
		// 	console.log('newValue: ', newValue);
		// 	console.log('oldValue: ', oldValue);
		// });

		const person = reactive({
			name: '홍길동',
			age: 30,
			hobby: '운동',
			obj: {
				count: 0,
			},
		});

		// watch(person, newValue => {
		// 	console.log('newValue: ', newValue);
		// });
		console.log(typeof person.obj);
    /** 즉, getter 는 getter 자신만 바뀌었냐 안바뀌었냐를 확인함 */
		watch(
			() => person.obj,
			newValue => {
				console.log('newValue: ', newValue);
			},
		);
		return { x, y, obj, person };
	},
};
</script>

<style lang="scss" scoped></style>
