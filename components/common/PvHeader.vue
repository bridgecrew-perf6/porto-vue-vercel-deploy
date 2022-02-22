<template>
	<header class="header">
		<div class="header-top bg-primary text-uppercase">
			<div class="container">
				<div class="header-left">
					<div class="header-dropdown mr-auto mr-sm-3 mr-md-0">
						<a
							href="javascript:;"
							class="pl-0"
						>
							<i class="flag-us flag"></i>ENG</a>

						<div class="header-menu">
							<ul>
								<li>
									<a href="javascript:;">
										<i class="flag-us flag mr-2"></i>ENG</a>
								</li>
								<li>
									<a href="javascript:;">
										<i class="flag-fr flag mr-2"></i>FRA</a>
								</li>
							</ul>
						</div>
					</div>
					<div class="header-dropdown ml-3 pl-1">
						<a href="javascript:;">USD</a>
						<div class="header-menu">
							<ul>
								<li>
									<a href="javascript:;">EUR</a>
								</li>
								<li>
									<a href="javascript:;">USD</a>
								</li>
							</ul>
						</div>
					</div>
				</div>

				<div class="header-right header-dropdowns ml-0 ml-sm-auto">
					<p class="top-message mb-0 d-none d-sm-block">Welcome To Porto!</p>
					<div class="header-dropdown dropdown-expanded mr-3">
						<a href="javascript:;">Links</a>
						<div class="header-menu">
							<ul>
								<li>
									<nuxt-link to="/pages/account">My Account</nuxt-link>
								</li>
								<li>
									<nuxt-link to="/pages/contact-us">Contact Us</nuxt-link>
								</li>
								<li>
									<nuxt-link to="/pages/wishlist">My Wishlist</nuxt-link>
								</li>
								<li>
									<a href="javascript:;">Site Map</a>
								</li>
								<li>
									<nuxt-link to="/pages/cart">Cart</nuxt-link>
								</li>
								<li>
									<nuxt-link
										to="/pages/login"
										class="login-link"
									>Log In</nuxt-link>
								</li>
							</ul>
						</div>
					</div>

					<span class="separator"></span>

					<div class="social-icons">
						<a
							href="javascript:;"
							class="social-icon social-facebook icon-facebook ml-0"
							
						></a>
						<a
							href="javascript:;"
							class="social-icon social-twitter icon-twitter ml-0"
							
						></a>
						<a
							href="javascript:;"
							class="social-icon social-instagram icon-instagram ml-0"
							
						></a>
					</div>
				</div>
			</div>
		</div>

		<div
			class="header-middle text-dark"
			:class="$route.path === '/' ? 'sticky-header' : 'sticky-header mobile-sticky'"
		>
			<div class="container">
				<div class="header-left col-lg-2 w-auto pl-0">
					<button
						class="mobile-menu-toggler mr-2"
						type="button"
						@click="showMobileMenu"
					>
						<i class="fas fa-bars"></i>
					</button>
					<nuxt-link
						to="/"
						class="logo"
					>
						<img
							src="~/static/images/logo.png"
							width="101"
							height="40"
							alt="Porto Logo"
						/>
					</nuxt-link>
				</div>

				<div class="header-right w-lg-max pl-2">
					<pv-header-search></pv-header-search>

					<div class="header-contact d-none d-lg-flex align-items-center pr-xl-5 mr-5 mr-xl-3 ml-5">
						<i class="icon-phone-2"></i>
						<h6 class="pt-1 line-height-1">
							Call us now
							<a
								href="tel:#"
								class="d-block text-dark ls-10 pt-1"
							>+123 5678 890</a>
						</h6>
					</div>

					<a
						href="javascript:;"
						@click="openLoginModal"
						class="header-icon header-icon-user"
						title="login"
					>
						<i class="icon-user-2"></i>
					</a>

					<nuxt-link
						to="/pages/wishlist"
						class="header-icon"
						title="wishlist"
					>
						<i class="icon-wishlist-2"></i>
					</nuxt-link>

					<pv-cart-menu></pv-cart-menu>
				</div>
			</div>
		</div>

		<div
			class="header-bottom sticky-header desktop-sticky d-none bg-gray"
			:class="$route.path !== '/' ? 'd-lg-block' : ''"
		>
			<div class="container">
				<div class="header-left">
					<nuxt-link
						to="/"
						class="logo"
					>
						<img
							:src="'./images/logo.png'"
							width="101"
							height="40"
						/>
					</nuxt-link>
				</div>
				<div class="header-center">
					<pv-main-menu></pv-main-menu>
				</div>
				<div class="header-right">
					<pv-header-search></pv-header-search>

					<a
						href="javascript:;"
						@click="openLoginModal"
						class="header-icon header-icon-user"
						title="login"
					>
						<i class="icon-user-2"></i>
					</a>

					<nuxt-link
						to="/pages/wishlist"
						class="header-icon"
						title="wishlist"
					>
						<i class="icon-wishlist-2"></i>
					</nuxt-link>

					<pv-cart-menu></pv-cart-menu>
				</div>
			</div>
		</div>
	</header>
</template>

<script>
import PvMainMenu from '~/components/common/partials/PvMainMenu';
import PvCartMenu from '~/components/common/partials/PvCartMenu';
import PvHeaderSearch from '~/components/common/partials/PvHeaderSearch';

document.querySelector('body').classList.add('loaded');

export default {
	components: {
		PvMainMenu,
		PvCartMenu,
		PvHeaderSearch
	},
	data: function() {
		return {
			isHome: {
				type: Boolean,
				default: true
			}
		};
	},
	methods: {
		openLoginModal: function() {
			this.$modal.show(
				() => import('~/components/features/modal/PvLoginModal'),
				{},
				{ width: '525', height: 'auto', adaptive: true }
			);
		},
		showMobileMenu: function() {
			document.querySelector('body').classList.add('mmenu-active');
		},
		showMobileSearch: function(e) {
			let headerSearch = e.currentTarget.closest('.header-search');
			headerSearch.classList.add('show');
			headerSearch
				.querySelector('.header-search-wrapper')
				.classList.add('show');
		}
	}
};
</script>