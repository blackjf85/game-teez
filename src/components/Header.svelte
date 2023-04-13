<script>
	import styles from '../styles/components/Header.module.css';
	import Logo from '../lib/images/Game_Teez_logo_rectangle--transparent.svg';
	import Hamburger from '../lib/images/Hamburger Icon.svg';
	import HamburgerMenu from './HamburgerMenu.svelte';

	let showMenu = false;

	function toggleMenu() {
		showMenu = !showMenu;
	}

	function closeMenu() {
		showMenu = false;
	}
</script>

<header class={styles.header}>
	<div class={styles.logo} aria-label="Site Logo">
		<a href="/">
			<img class={styles.logo__image} src={Logo} alt="Site Logo" />
		</a>
	</div>
	<button class={styles.hamburger} aria-label="Open Navigation" on:click={toggleMenu}>
		<img class={styles.hamburger__image} src={Hamburger} alt="Open Navigation" />
	</button>
	<HamburgerMenu bind:showMenu on:close={closeMenu} />
	<nav class={`${styles.navigation} ${showMenu ? styles.show : ''}`} aria-label="Main Navigation">
		<ul class={styles.navigation__list}>
			<li class={styles.navigation__item}>
				<a href="/" class={styles.navigation__link}>Home</a>
			</li>
			<li class={styles.navigation__item}>
				<a href="/about" class={styles.navigation__link}>About</a>
			</li>
			<li class={styles.navigation__item}>
				<a href="/contact" class={styles.navigation__link}>Contact</a>
			</li>
			<li class={styles.navigation__item}>
				<a href="/shop" class={styles.navigation__link}>Shop</a>
			</li>
		</ul>
	</nav>
</header>
