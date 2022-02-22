<template>
	<aside class="sidebar-home col-lg-3 order-lg-first mobile-sidebar">
		<div class="side-menu-wrapper text-uppercase mb-2 d-none d-lg-block">
			<h2 class="side-menu-title bg-gray ls-n-25">Browse Categories</h2>

			<nav class="side-nav">
				<ul class="menu menu-vertical sf-arrows">
					<li :class="{active: isHomeActive}">
						<nuxt-link to="/">
							<i class="icon-home"></i>Home
						</nuxt-link>
					</li>

					<li :class="{active: $route.path.indexOf('/shop') > -1}">
						<nuxt-link
							to="/shop"
							class="sf-with-ul"
							:class="{active: $route.path.indexOf('/shop') > -1}"
						>
							<i class="sicon-badge"></i>Categories
						</nuxt-link>

						<div class="megamenu megamenu-fixed-width megamenu-3cols">
							<div class="row">
								<div class="col-lg-4">
									<a
										href="javascript:;"
										class="nolink"
									>VARIATION 1</a>

									<ul class="submenu">
										<li
											v-for="item in mainMenu.shop.variation1"
											:key="item.id"
										>
											<nuxt-link :to="item.url">
												{{ item.title }}
												<span
													class="tip tip-hot"
													v-if="item.hot"
												>Hot</span>
											</nuxt-link>
										</li>
									</ul>
								</div>

								<div class="col-lg-4">
									<a
										href="javascript:;"
										class="nolink"
									>VARIATION 2</a>

									<ul class="submenu">
										<li
											v-for="item in mainMenu.shop.variation2"
											:key="item.id"
										>
											<nuxt-link :to="item.url">{{ item.title }}</nuxt-link>
										</li>
									</ul>
								</div>

								<div class="col-lg-4 p-0">
									<div class="menu-banner">
										<figure>
											<img
												src="~/static/images/menu-banner.jpg"
												alt="Menu banner"
												width="300"
												height="300"
											/>
										</figure>
										<div class="banner-content">
											<h4>
												<span class>UP TO</span>
												<br />
												<b class>50%</b>
												<i>OFF</i>
											</h4>
											<nuxt-link
												to="/shop"
												class="btn btn-sm btn-dark"
											>SHOP NOW</nuxt-link>
										</div>
									</div>
								</div>
							</div>
						</div>
					</li>

					<li :class="{active: $route.path.indexOf('/product') > -1}">
						<nuxt-link
							to="/product/default/basketball-sports-blue-shoes"
							class="sf-with-ul"
							:class="{active: $route.path.indexOf('/product') > -1}"
						>
							<i class="sicon-basket"></i>Products
						</nuxt-link>

						<div class="megamenu megamenu-fixed-width megamenu-3cols">
							<div class="row">
								<div class="col-lg-4">
									<a
										href="javascript:;"
										class="nolink"
									>PRODUCT PAGES</a>

									<ul class="submenu">
										<li
											v-for="item in mainMenu.product.pages"
											:key="item.title"
										>
											<nuxt-link :to="item.url">
												{{ item.title }}
												<span
													class="tip tip-hot"
													v-if="item.hot"
												>Hot</span>
											</nuxt-link>
										</li>
									</ul>
								</div>

								<div class="col-lg-4">
									<a
										href="javascript:;"
										class="nolink"
									>PRODUCT LAYOUTS</a>

									<ul class="submenu">
										<li
											v-for="item in mainMenu.product.layout"
											:key="item.title"
										>
											<nuxt-link :to="item.url">{{ item.title }}</nuxt-link>
										</li>

										<li>
											<a href="javascript:;">Build your own</a>
										</li>
									</ul>
								</div>

								<div class="col-lg-4 p-0">
									<div class="menu-banner menu-banner-2 position-relative">
										<figure>
											<img
												src="~/static/images/menu-banner-1.jpg"
												alt="Menu banner"
												class="product-promo"
												width="380"
												height="790"
											/>
										</figure>
										<i>OFF</i>
										<div class="banner-content">
											<h4>
												<span class>UP TO</span>
												<br />
												<b class>50%</b>
											</h4>
										</div>
										<nuxt-link
											to="/shop"
											class="btn btn-sm btn-dark"
										>SHOP NOW</nuxt-link>
									</div>
								</div>
							</div>
						</div>
					</li>

					<li :class="{active: isPageItemActived}">
						<a
							href="javascript:;"
							class="sf-with-ul"
							:class="{active: isPageItemActived}"
						>
							<i class="sicon-envelope"></i>Pages
						</a>

						<ul>
							<li
								v-for="item in mainMenu.other"
								:key="item.title"
							>
								<nuxt-link
									:to="item.url"
									:class="{'sub-menu-link': item.subPages}"
								>{{ item.title }}</nuxt-link>

								<ul v-if="item.subPages">
									<li
										v-for="subItem in item.subPages"
										:key="subItem.title"
									>
										<nuxt-link :to="subItem.url">{{ subItem.title }}</nuxt-link>
									</li>
								</ul>
							</li>
						</ul>
					</li>

					<li :class="{active: $route.path.indexOf('/pages/blog') > -1}">
						<nuxt-link
							to="/pages/blog"
							:class="{active: $route.path.indexOf('/pages/blog') > -1}"
						>
							<i class="sicon-book-open"></i>Blog
						</nuxt-link>
					</li>
					<li>
						<nuxt-link to="/pages/about-us">
							<i class="sicon-users"></i>About Us
						</nuxt-link>
					</li>
					<li>
						<a href="javascript:;">
							<i class="icon-cat-gift"></i>Special Offer!
						</a>
					</li>
					<li>
						<a
							href="/https://1.envato.market/DdLk5"
							target="_blank"
						>
							<i class="sicon-star"></i>Buy Porto!<span class="tip tip-hot">Hot</span>
						</a>
					</li>
				</ul>
			</nav>
		</div>

		<div class="widget widget-banners px-3 pb-3 text-center">
			<pv-carousel
				class="dots-small"
				:options="homeSidebarSlider"
			>
				<div class="banner d-flex flex-column align-items-center swiper-slide">
					<h3 class="badge-sale bg-primary d-flex flex-column align-items-center justify-content-center text-uppercase">
						<em>Sale</em>Many Item
					</h3>

					<h4 class="sale-text text-uppercase">
						<small>UP TO</small>50<sup>%</sup>
						<sub>off</sub>
					</h4>
					<p>Bags, Clothing, T-Shirts, Shoes, Watches and much more...</p>
					<nuxt-link
						to="/shop"
						class="btn btn-dark btn-md"
					>VIEW SALE</nuxt-link>
				</div>

				<div class="banner banner4 swiper-slide">
					<figure>
						<img
							:src="'./images/home/banners/banner-7.jpg'"
							alt="banner"
						/>
					</figure>

					<div class="banner-layer">
						<div class="coupon-sale-content">
							<h4>DRONE + CAMERAS</h4>
							<h5 class="coupon-sale-text text-gray ls-n-10 p-0 font1">
								<i>
									UP
									TO
								</i>
								<b class="text-white bg-dark font1">$100</b> OFF
							</h5>
							<p class="ls-0">Top Brands and Models!</p>
							<nuxt-link
								to="/shop"
								class="btn btn-inline-block btn-dark btn-black ls-0"
							>VIEW SALE</nuxt-link>
						</div>
					</div>
				</div>

				<div class="banner banner5 swiper-slide">
					<h4>HEADPHONES SALE</h4>

					<figure class="m-b-3">
						<img
							:src="'./images/home/banners/banner-8.jpg'"
							alt="banner"
						/>
					</figure>

					<div class="banner-layer">
						<div class="coupon-sale-content">
							<h5 class="coupon-sale-text ls-n-10 p-0 font1">
								<i>UP TO</i>
								<b class="text-white bg-secondary font1">50%</b> OFF
							</h5>
							<nuxt-link
								to="/shop"
								class="btn btn-inline-block btn-dark btn-black ls-0"
							>VIEW SALE</nuxt-link>
						</div>
					</div>
				</div>
			</pv-carousel>
		</div>

		<div class="widget widget-newsletters bg-gray text-center">
			<h3 class="widget-title text-uppercase m-b-3">Subscribe Newsletter</h3>
			<p class="mb-2">Get all the latest information on Events, Sales and Offers.</p>
			<form action="#">
				<div class="form-group position-relative sicon-envolope-letter">
					<input
						type="email"
						class="form-control"
						name="newsletter-email"
						placeholder="Email address"
						required
					/>
				</div>
				<input
					type="submit"
					class="btn btn-primary btn-md"
					value="Subscribe"
				/>
			</form>
		</div>

		<div class="widget widget-testimonials">
			<pv-carousel
				class="dots-left dots-small"
				:options="homeSidebarSlider"
			>
				<div class="testimonial swiper-slide">
					<div class="testimonial-owner">
						<figure>
							<img
								:src="'./images/clients/client-1.jpg'"
								alt="client"
							/>
						</figure>

						<div>
							<h4 class="testimonial-title">john Smith</h4>
							<span>CEO &amp; Founder</span>
						</div>
					</div>

					<blockquote class="ml-4 pr-0">
						<p>
							Lorem ipsum dolor sit amet, consectetur elitad adipiscing Cras non placerat
							mi.
						</p>
					</blockquote>
				</div>

				<div class="testimonial swiper-slide">
					<div class="testimonial-owner">
						<figure>
							<img
								:src="'./images/clients/client-2.jpg'"
								alt="client"
							/>
						</figure>

						<div>
							<h4 class="testimonial-title">Dae Smith</h4>
							<span>CEO &amp; Founder</span>
						</div>
					</div>

					<blockquote class="ml-4 pr-0">
						<p>
							Lorem ipsum dolor sit amet, consectetur elitad adipiscing Cras non placerat
							mi.
						</p>
					</blockquote>
				</div>

				<div class="testimonial swiper-slide">
					<div class="testimonial-owner">
						<figure>
							<img
								:src="'./images/clients/client-3.jpg'"
								alt="client"
							/>
						</figure>

						<div>
							<h4 class="testimonial-title">John Doe</h4>
							<span>CEO &amp; Founder</span>
						</div>
					</div>

					<blockquote class="ml-4 pr-0">
						<p>
							Lorem ipsum dolor sit amet, consectetur elitad adipiscing Cras non placerat
							mi.
						</p>
					</blockquote>
				</div>
			</pv-carousel>
		</div>

		<div class="widget widget-posts post-date-in-media media-with-zoom mb-lg-2 pb-lg-2">
			<pv-carousel
				class="dots-left dots-m-0 dots-small"
				:options="homeSidebarSlider"
			>
				<pv-post-four
					class="swiper-slide"
					v-for="(post,index) in posts"
					:key="'post' + index"
					:post="post"
					:is-magnify="true"
				></pv-post-four>
			</pv-carousel>
		</div>
	</aside>
</template>

<script>
import Sticky from 'vue-sticky-directive';
import PvCarousel from '~/components/features/PvCarousel';
import PvPostFour from '~/components/features/post/PvPostFour';
import { homeSidebarSlider } from '~/utils/data/carousel';
import { mainMenu } from '~/utils/data/menu';

export default {
	components: {
		PvCarousel,
		PvPostFour
	},
	directives: {
		Sticky
	},
	props: {
		featuredProducts: Array,
		posts: Array
	},
	data: function() {
		return {
			isSticky: false,
			homeSidebarSlider: homeSidebarSlider,
			isHomeActive: false,
			mainMenu
		};
	},
	computed: {
		categoryTree: function() {
			return new Tree(this.categoryList);
		},
		isPageItemActived: function() {
			let exItems = ['blog', 'about-us', 'contact-us'];
			if (
				this.$route.path.includes('/pages') &&
				exItems.findIndex(item => this.$route.path.includes(item)) ===
					-1
			) {
				return true;
			}

			return false;
		}
	},
	mounted: function() {
		this.resizeHandler();
		window.addEventListener('resize', this.resizeHandler, {
			passive: true
		});

		if (
			document.querySelector('.menu-vertical > li:first-child > a.active')
		)
			this.isHomeActive = true;
		else this.isHomeActive = false;

		let items = document.querySelectorAll('.menu-vertical > li');
		items.forEach(item => {
			item.addEventListener('mouseenter', this.mouseOverHandler);
			item.addEventListener('mouseleave', this.mouseLeaveHandler);
		});
	},
	destroyed: function() {
		window.removeEventListener('resize', this.resizeHandler);

		let items = document.querySelectorAll('.sf-with-ul');
		items.forEach(item => {
			item.removeEventListener('mouseover', this.mouseOverHandler);
			item.removeEventListener('mouseleave', this.mouseLeaveHandler);
		});
	},
	methods: {
		resizeHandler: function() {
			this.isSticky = window.innerWidth > 991 ? true : false;
		},
		mouseOverHandler: function(e) {
			let currentTarget = e.currentTarget;
			let item;

			currentTarget.classList.add('show');
			if (e.currentTarget.querySelector('.megamenu')) {
				item = e.currentTarget.querySelector('.megamenu');
			} else if (e.currentTarget.querySelector('ul')) {
				item = e.currentTarget.querySelector('ul');
			}
			if (item) {
				setTimeout(() => {
					if (currentTarget.classList.contains('show')) {
						item.setAttribute(
							'style',
							'left: 90%; display: block; opacity: 0;'
						);
					}
				}, 50);
				setTimeout(() => {
					if (currentTarget.classList.contains('show')) {
						item.setAttribute(
							'style',
							'left: 100%; display: block; opacity: 1;'
						);
					} else item.setAttribute('style', '');
				}, 100);
			}
		},
		mouseLeaveHandler: function(e) {
			e.currentTarget.classList.remove('show');
			if (e.currentTarget.querySelector('.megamenu'))
				e.currentTarget
					.querySelector('.megamenu')
					.setAttribute('style', '');
			if (e.currentTarget.querySelector('ul'))
				e.currentTarget.querySelector('ul').setAttribute('style', '');
		}
	}
};
</script>