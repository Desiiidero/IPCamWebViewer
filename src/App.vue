<script setup>
import { ref } from "vue";

let obj = new Map();
obj.set("東區廠", [
			"https://cctvp02.freeway.gov.tw/mjpeg/X01001602800401",
			"https://cctvn.freeway.gov.tw/abs2mjpg/bmjpg?camera=95020",
			"https://cctvn.freeway.gov.tw/abs2mjpg/bmjpg?camera=15771",
			"https://cctvn.freeway.gov.tw/abs2mjpg/bmjpg?camera=15370",
			"https://cctvs.freeway.gov.tw/live-view/mjpg/video.cgi?camera=477",
			"https://cctvn.freeway.gov.tw/abs2mjpg/bmjpg?camera=40570",
			"https://cctvn.freeway.gov.tw/abs2mjpg/bmjpg?camera=71930",
			"https://cctvs.freeway.gov.tw/live-view/mjpg/video.cgi?camera=406"
		]);
obj.set("南區廠", [
			"https://cctvp02.freeway.gov.tw/mjpeg/X01001510110801",
			"https://cctvc.freeway.gov.tw/abs2mjpg/bmjpg?camera=859",
			"https://cctvc.freeway.gov.tw/abs2mjpg/bmjpg?camera=165",
			"https://cctvc.freeway.gov.tw/abs2mjpg/bmjpg?camera=893",
			"https://cctvs.freeway.gov.tw/live-view/mjpg/video.cgi?camera=305",
			"https://cctvn.freeway.gov.tw/abs2mjpg/bmjpg?camera=33120"
		]);
obj.set("北區廠", [
			"https://cctvn.freeway.gov.tw/abs2mjpg/bmjpg?camera=14330",
			"https://cctvn.freeway.gov.tw/abs2mjpg/bmjpg?camera=13290",
			"https://cctvs.freeway.gov.tw/live-view/mjpg/video.cgi?camera=460",
			"https://cctvs.freeway.gov.tw/live-view/mjpg/video.cgi?camera=344",
			"https://cctvc.freeway.gov.tw/abs2mjpg/bmjpg?camera=28"
		]);
obj.set("遠得要命王國名字還很長", [
			"https://cctvn.freeway.gov.tw/abs2mjpg/bmjpg?camera=40640",
			"https://cctvs.freeway.gov.tw/live-view/mjpg/video.cgi?camera=329",
			"https://cctvc.freeway.gov.tw/abs2mjpg/bmjpg?camera=413",
			"https://cctvc.freeway.gov.tw/abs2mjpg/bmjpg?camera=352",
			"https://cctvc.freeway.gov.tw/abs2mjpg/bmjpg?camera=207"
		]);

const [ first ] = obj.values();
let itemList = ref(first);
const place = ref([
	"東區廠",
	"南區廠",
	"北區廠",
	"遠得要命王國名字還很長"
]);
let selectedValue = ref("東區廠");

function onChanged() {
	itemList.value = obj.get(selectedValue.value);
	console.log(itemList.value);
}
</script>

<template>
	<section class="filter flex space-x-4 my-3 m-auto justify-center items-center">
		<span>廠區選擇：</span>
		<select class="box" v-on:change="onChanged()" v-model="selectedValue">
			<option v-for="item in place">{{ item }}</option>
		</select>
	</section>
	<section class="camera pt-5 px-10 pb-20 min-h-screen">
		<div class="camera-wrap">
			<img v-for="item in itemList" v-bind:src="item">
		</div>
	</section>
</template>
