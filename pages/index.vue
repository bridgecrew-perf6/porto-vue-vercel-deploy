<template>
	<main class="main home">
		<div class="container mb-2">
			<pv-service-section></pv-service-section>

			<div class="row">
				<div class="col-lg-9">
					<pv-intro-section></pv-intro-section>

					<pv-banner-section></pv-banner-section>

					<pv-featured-collection
						:products="featuredProducts"
						v-if="featuredProducts"
					></pv-featured-collection>

					<pv-brand-section></pv-brand-section>

					<pv-small-collection
						:best-products="bestProducts.slice(0,3)"
						:latest-products="newProducts.slice(0,3)"
						:top-rated-products="topRatedProducts.slice(0,3)"
						:is-featured="false"
					></pv-small-collection>

					<hr class="mt-1 mb-3 pb-2" />

					<pv-feature-section></pv-feature-section>
				</div>

				<div
					class="sidebar-overlay"
					@click.prevent="toggleSidebar"
				></div>
				<div
					class="sidebar-toggle custom-sidebar-toggle"
					@click.prevent="toggleSidebar"
				>
					<i class="fas fa-sliders-h"></i>
				</div>

				<pv-home-sidebar :posts="posts"></pv-home-sidebar>

				<light-box
					v-if="lightBoxMedia.length > 0"
					ref="lightBox"
					:media="lightBoxMedia"
					:show-light-box="false"
				/>
			</div>
		</div>
	</main>
</template>

<script>
import PvServiceSection from '~/components/partials/home/PvServiceSection';
import PvHomeSidebar from '~/components/partials/home/PvHomeSidebar';
import PvIntroSection from '~/components/partials/home/PvIntroSection';
import PvBannerSection from '~/components/partials/home/PvBannerSection';
import PvBrandSection from '~/components/partials/home/PvBrandSection';
import PvFeaturedCollection from '~/components/partials/home/PvFeaturedCollection';
import PvFeatureSection from '~/components/partials/home/PvFeatureSection';
import PvSmallCollection from '~/components/partials/product/PvSmallCollection';
import LightBox from 'vue-image-lightbox';

import {
	getProductsByAttri,
	getTopSellingProducts,
	getTopRatedProducts
} from '~/utils/service';
import { getCookie } from '~/utils';
import Api, { baseUrl } from '~/api';

export default {
	components: {
		PvIntroSection,
		PvServiceSection,
		PvBannerSection,
		PvFeatureSection,
		PvBrandSection,
		PvFeaturedCollection,
		PvSmallCollection,
		PvHomeSidebar,
		LightBox
	},
	data: function() {
		return {
			products: [],
			posts: [],
			featuredProducts: [],
			newProducts: [],
			bestProducts: [],
			topRatedProducts: []
		};
	},
	computed: {
		lightBoxMedia: function() {
			let pictures = [];
			for (let i = 0; i < this.posts.length; i++) {
				pictures.push(this.posts[i].picture[0]);
			}
			return pictures.reduce((acc, cur) => {
				return [
					...acc,
					{
						src: `${baseUrl}${cur.url}`,
						thumb: `${baseUrl}${cur.url}`
					}
				];
			}, []);
		}
	},
	mounted: function() {
		Api.get(`${baseUrl}/demo1`)
			.then(response => {
				this.products = response.data.products;
				this.posts = response.data.posts;
				this.featuredProducts = getProductsByAttri(
					response.data.products
				);
				this.newProducts = getProductsByAttri(
					response.data.products,
					'is_new'
				);
				this.bestProducts = getTopSellingProducts(
					response.data.products
				);
				this.topRatedProducts = getTopRatedProducts(
					response.data.products
				);
			})
			.catch(error => ({ error: JSON.stringify(error) }));

		this.timerId = setTimeout(() => {
			if (
				this.$route.path === '/' &&
				getCookie('newsletter') !== 'false'
			) {
				this.$modal.show(
					() =>
						import('~/components/features/modal/PvNewsletterModal'),
					{},
					{
						width: '740',
						height: 'auto',
						adaptive: true,
						class: 'newsletter-modal'
					}
				);
			}
		}, 10000);
	},
	destroyed: function() {
		clearTimeout(this.timerId);
	},
	methods: {
		toggleSidebar: function() {
			let body = document.querySelector('body');
			if (body.classList.contains('sidebar-opened')) {
				body.classList.remove('sidebar-opened');
			} else {
				body.classList.add('sidebar-opened');
			}
		}
	}
};
</script>