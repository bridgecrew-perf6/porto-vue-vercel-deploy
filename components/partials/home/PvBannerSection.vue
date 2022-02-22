<template>
	<pv-carousel
		class="banners-container m-b-2"
		:options="bannerSlider"
	>
		<div
			class="banner banner1 banner-hover-shadow d-flex align-items-center mb-2 appear-animate swiper-slide"
			data-animation-name="fadeInLeftShorter"
			data-animation-delay="500"
			v-animate
		>
			<figure class="w-100">
				<img
					v-lazy="'./images/home/banners/banner-1.jpg'"
					alt="banner"
					width="280"
					height="170"
					image-ratio="60.71"
					style="background: #dadada"
				/>
			</figure>
			<div class="banner-layer">
				<h3 class="m-b-2">Porto Watches</h3>
				<h4 class="m-b-4 text-primary">
					<sup class="text-dark">
						<del>20%</del>
					</sup>30%<sup>OFF</sup>
				</h4>
				<nuxt-link
					to="/shop"
					class="text-dark text-uppercase ls-10"
				>Shop Now</nuxt-link>
			</div>
		</div>

		<div
			class="banner banner2 text-uppercase banner-hover-shadow d-flex align-items-center mb-2 appear-animate swiper-slide"
			v-animate
			data-animation-name="fadeInUpShorter"
			data-animation-delay="200"
		>
			<figure class="w-100">
				<img
					v-lazy="'./images/home/banners/banner-2.jpg'"
					alt="banner"
					width="280"
					height="141"
					image-ratio="50.35"
				/>
			</figure>
			<div class="banner-layer text-center">
				<h3 class="m-b-1 ls-n-20">Deal Promos</h3>
				<h4 class="text-body">Starting at $99</h4>
				<nuxt-link
					to="/shop"
					class="text-dark text-uppercase ls-10"
				>Shop Now</nuxt-link>
			</div>
		</div>

		<div
			class="banner banner3 banner-hover-shadow d-flex align-items-center mb-2 appear-animate swiper-slide"
			data-animation-name="fadeInRightShorter"
			data-animation-delay="500"
			v-animate
		>
			<figure class="w-100">
				<img
					:src="'./images/home/banners/banner-3.jpg'"
					alt="banner"
					width="280"
					height="170"
					image-ratio="60.71"
					style="background: #dadada"
				/>
			</figure>
			<div class="banner-layer text-right">
				<h3 class="m-b-2">Handbags</h3>
				<h4 class="mb-3 text-secondary text-uppercase">Starting at $99</h4>
				<nuxt-link
					to="/shop"
					class="text-dark text-uppercase ls-10"
				>Shop Now</nuxt-link>
			</div>
		</div>
	</pv-carousel>
</template>

<script>
import PvCarousel from '~/components/features/PvCarousel';
import { bannerSlider } from '~/utils/data/carousel';
export default {
	components: {
		PvCarousel
	},
	data: function() {
		return {
			bannerSlider: bannerSlider
		};
	}
};
</script>