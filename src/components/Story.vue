<template>
	<v-container class="black" fluid pa-0>
		<v-sheet class="mx-auto" v-for="i in len" :key="i" max-width="750px" style="position:relative">
			<v-img :src="require('../assets/RAW/' + i + '.webp')" eager style="z-index: 0"/>
			<v-img
				:src="TLimg(i)"
				style="z-index: 1; position:absolute; top:0"
				v-show="num"
				eager
			/>
		</v-sheet>
	</v-container>
</template>

<script>
export default {
	name: "Story",
	props: [ "num" ],
	data: () => ({ len: 0 }),
	methods: {
		piclen() {
			const illustrations = require.context("../assets/RAW/", false, /^.*\.webp$/);
			this.len = illustrations.keys().length;
		},
		TLimg(i){
			try {
				return require('../assets/TL/TL' + i + '.png');
			} catch (e) {
				return require('../assets/TL/TLBlank.png');
			}
		}
	},
	created() {
		this.piclen();
	},
};
</script>
