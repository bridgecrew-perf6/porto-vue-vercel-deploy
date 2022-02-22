<template>
	<main class="main skeleton-body">
		<div class="container">
			<nav
				aria-label="breadcrumb"
				class="breadcrumb-nav"
			>
				<ol class="breadcrumb">
					<li class="breadcrumb-item">
						<nuxt-link to="/">
							<i class="icon-home"></i>
						</nuxt-link>
					</li>
					<li class="breadcrumb-item active">Shop</li>
				</ol>
			</nav>

			<div class="row">
				<div class="col-lg-9">
					<pv-carousel
						:options="baseSlider6"
						class="category-home-slider home-slider"
					>
						<div class="home-slide home-slide1 banner banner-md-vw banner-sm-vw d-flex align-items-center swiper-slide">
							<img
								class="slide-bg"
								:src="'./images/home/banners/banner-4.jpg'"
								width="880"
								height="280"
								style="background: #6db2db; background-size: contain; background-repeat: no-repeat; background-position: 100% 100%;"
								alt="category-banenr"
							/>
							<div class="banner-layer">
								<h4 class="text-white mb-0">Find the Boundaries. Push Through!</h4>
								<h2 class="text-white mb-0">Summer Sale</h2>
								<h3 class="text-white text-uppercase m-b-3">30% Off</h3>
								<h5 class="text-white text-uppercase d-inline-block mb-0 ls-n-20 align-text-bottom">
									Starting At
									<b class="coupon-sale-text bg-white text-secondary d-inline-block">
										$
										<em class="align-text-top">199</em>99
									</b>
								</h5>
								<a
									href="javascript:;"
									class="btn btn-dark btn-md"
								>GET YOURS!</a>
							</div>
						</div>

						<div class="home-slide home-slide2 banner banner-md-vw banner-sm-vw d-flex align-items-center swiper-slide">
							<img
								class="slide-bg"
								:src="'./images/home/banners/banner-5.jpg'"
								width="880"
								height="280"
								alt="category-banenr"
							/>
							<div class="banner-layer text-uppercase">
								<h4 class="m-b-2">Over 200 products with discounts</h4>
								<h2 class="m-b-3">Great Deals</h2>
								<h5 class="d-inline-block mb-0 align-top mr-3 mb-2">
									Starting At
									<b>
										$
										<em>299</em>99
									</b>
								</h5>
								<a
									href="javascript:;"
									class="btn btn-dark btn-md"
								>Get Yours!</a>
							</div>
						</div>

						<div class="home-slide home-slide3 banner banner-md-vw banner-sm-vw d-flex align-items-center swiper-slide">
							<img
								class="slide-bg"
								:src="'./images/home/banners/banner-6.jpg'"
								width="880"
								height="280"
								alt="category-banenr"
							/>
							<div class="banner-layer text-uppercase">
								<h4 class="m-b-2">Up to 70% off</h4>
								<h2 class="m-b-3">New Arrivals</h2>
								<h5 class="d-inline-block mb-0 align-top mr-4 pr-3 mb-2 ml-0">
									Starting At
									<b>
										$
										<em>299</em>99
									</b>
								</h5>
								<a
									href="javascript:;"
									class="btn btn-dark btn-md"
								>Get Yours!</a>
							</div>
						</div>
					</pv-carousel>

					<pv-product-list-one :category-list="categoryList"></pv-product-list-one>
				</div>

				<div
					class="sidebar-overlay"
					@click="hideSidebar"
				></div>
				<aside
					class="sidebar-shop col-lg-3 order-lg-first mobile-sidebar"
					sticky-container
				>
					<div
						v-sticky="isSticky"
						sticky-offset="{top: 68}"
					>
						<pv-sidebar-filter-one
							:category-list="categoryList"
							:featured-products="featuredProducts"
							v-if="featuredProducts.length > 0"
						></pv-sidebar-filter-one>

						<div
							class="sidebar-content skeleton-body"
							v-if="featuredProducts.length === 0"
						>
							<aside class="widget"></aside>
							<aside class="widget"></aside>
							<aside class="widget"></aside>
						</div>
					</div>
				</aside>
			</div>

			<div class="mb-4"></div>
		</div>
	</main>
</template>

<script>
import { VueTreeList, Tree } from 'vue-tree-list';
import Sticky from 'vue-sticky-directive';
import PvCarousel from '~/components/features/PvCarousel';
import PvSidebarFilterOne from '~/components/partials/shop/sidebar-filter/PvSidebarFilterOne';
import PvProductListOne from '~/components/partials/shop/product-list/PvProductListOne';
import Api, { baseUrl, currentDemo } from '~/api';
import { baseSlider6 } from '~/utils/data/carousel';

export default {
	directives: {
		Sticky
	},
	components: {
		PvSidebarFilterOne,
		PvProductListOne,
		PvCarousel
	},
	data: function() {
		return {
			categoryList: [],
			featuredProducts: [],
			baseSlider6: baseSlider6,
			isSticky: false
		};
	},
	mounted: function() {
		this.getCategoryLists();
		this.resizeHandler();
		window.addEventListener('resize', this.resizeHandler, {
			passive: true
		});
	},
	destroyed: function() {
		window.removeEventListener('resize', this.resizeHandler);
	},
	methods: {
		getCategoryLists: function() {
			Api.get(`${baseUrl}/shop/sidebar-list`, {
				params: { demo: currentDemo }
			})
				.then(response => {
					this.categoryList = response.data.sidebarList;
					this.featuredProducts = response.data.featuredProducts;
				})
				.catch(error => ({ error: JSON.stringify(error) }));
		},
		resizeHandler: function() {
			this.isSticky = window.innerWidth > 991 ? true : false;
		},
		hideSidebar: function() {
			document.querySelector('body').classList.remove('sidebar-opened');
		}
	}
};
</script>