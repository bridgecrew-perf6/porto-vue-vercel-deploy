<template>
	<pv-carousel
		class="brands-slider images-center appear-animate"
		data-animation-name="fadeIn"
		data-animation-duration="500"
		v-animate
		:options="brandSlider"
	>
		<div class="swiper-slide">
			<img
				:src="'./images/brands/small/brand1.png'"
				width="140"
				height="60"
				alt="brand"
			/>
		</div>

		<div class="swiper-slide">
			<img
				:src="'./images/brands/small/brand2.png'"
				width="140"
				height="60"
				alt="brand"
			/>
		</div>

		<div class="swiper-slide">
			<img
				:src="'./images/brands/small/brand3.png'"
				width="140"
				height="60"
				alt="brand"
			/>
		</div>

		<div class="swiper-slide">
			<img
				:src="'./images/brands/small/brand4.png'"
				width="140"
				height="60"
				alt="brand"
			/>
		</div>

		<div class="swiper-slide">
			<img
				:src="'./images/brands/small/brand5.png'"
				width="140"
				height="60"
				alt="brand"
			/>
		</div>

		<div class="swiper-slide">
			<img
				:src="'./images/brands/small/brand6.png'"
				width="140"
				height="60"
				alt="brand"
			/>
		</div>
	</pv-carousel>
</template>

<script>
import PvCarousel from '~/components/features/PvCarousel';
import { brandSlider } from '~/utils/data/carousel';

export default {
	components: {
		PvCarousel
	},
	data: function() {
		return {
			brandSlider: brandSlider
		};
	}
};
</script>