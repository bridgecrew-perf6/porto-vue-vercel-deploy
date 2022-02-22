<template>
	<pv-carousel
		class="home-slider slide-animate mb-2"
		:options="homeSidebarSlider"
		v-animate
	>
		<div class="home-slide home-slide1 banner banner-md-vw banner-sm-vw d-flex align-items-center swiper-slide">
			<img
				class="slide-bg"
				src="~/static/images/home/slider/slide-1.png"
				alt="slider image"
				width="880"
				height="428"
				image-ratio="48.63"
			/>
			<div
				class="banner-layer appear-animate"
				data-animation-name="fadeInUpShorter"
			>
				<h4 class="text-white mb-0">Find the Boundaries. Push Through!</h4>
				<h2 class="text-white mb-0">Summer Sale</h2>
				<h3 class="text-white text-uppercase m-b-3">70% Off</h3>
				<h5 class="text-white text-uppercase d-inline-block mb-0 ls-n-20 align-text-bottom">
					Starting At
					<b class="coupon-sale-text bg-secondary text-white d-inline-block">$<em class="align-text-top">199</em>99
					</b>
				</h5>
				<nuxt-link
					to="/shop"
					class="btn btn-dark btn-md ls-10"
				>Shop Now!</nuxt-link>
			</div>
		</div>

		<div class="home-slide home-slide2 banner banner-md-vw banner-sm-vw d-flex align-items-center swiper-slide">
			<img
				class="slide-bg"
				src="~/static/images/home/slider/slide-2.jpg"
				alt="slider image"
				width="880"
				height="428"
				image-ratio="48.63"
			/>
			<div
				class="banner-layer text-uppercase appear-animate"
				data-animation-name="fadeInUpShorter"
			>
				<h4 class="m-b-2">Over 200 products with discounts</h4>
				<h2 class="m-b-3">Great Deals</h2>
				<h5 class="d-inline-block mb-0 align-top mr-5 mb-2">
					Starting At
					<b>
						$
						<em>299</em>99
					</b>
				</h5>
				<nuxt-link
					to="/shop"
					class="btn btn-dark btn-md ls-10"
				>Get Yours!</nuxt-link>
			</div>
		</div>

		<div class="home-slide home-slide3 banner banner-md-vw banner-sm-vw d-flex align-items-center swiper-slide">
			<img
				class="slide-bg"
				src="~/static/images/home/slider/slide-3.jpg"
				alt="slider image"
				width="880"
				height="428"
				image-ratio="48.63"
			/>
			<div
				class="banner-layer text-uppercase appear-animate"
				data-animation-name="fadeInUpShorter"
			>
				<h4 class="m-b-2">Up to 70% off</h4>
				<h2 class="m-b-3">New Arrivals</h2>
				<h5 class="d-inline-block mb-0 align-top mr-5 mb-2">
					Starting At
					<b>
						$
						<em>299</em>99
					</b>
				</h5>
				<nuxt-link
					to="/shop"
					class="btn btn-dark btn-md ls-10"
				>Get Yours!</nuxt-link>
			</div>
		</div>
	</pv-carousel>
</template>

<script>
import PvCarousel from '~/components/features/PvCarousel';
import { homeSidebarSlider } from '~/utils/data/carousel';

export default {
	components: {
		PvCarousel
	},
	data: function() {
		return {
			homeSidebarSlider: homeSidebarSlider
		};
	}
};
</script>