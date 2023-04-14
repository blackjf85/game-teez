<script>
	import { onMount } from 'svelte';
	import styles from '../styles/components/Hero.module.css';
	let hero;

	async function checkWebpSupport() {
		if (!self.createImageBitmap) return false;

		const webpData = 'data:image/webp;base64,UklGRhoAAABXRUJQVlA4TA0AAAAvAAAAEAcQERGIiP4HAA==';
		const blob = await fetch(webpData).then((r) => r.blob());
		return createImageBitmap(blob).then(
			() => true,
			() => false
		);
	}

	onMount(async () => {
		if (await checkWebpSupport()) {
			hero.classList.add(styles['hero--webp']);
		}
	});
</script>

<div class={`${styles.hero}`} bind:this={hero}>
	<div class={styles.hero__content}>
		<h1 class={styles.hero__heading} aria-label="GameTeez">
			Game<span class={styles.hero__headingAccent}>Teez</span>
		</h1>
		<h2 class={styles.hero__subheading} aria-label="Power-Up Your Wardrobe">
			Power-Up Your Wardrobe
		</h2>
		<p
			class={styles.hero__text}
			aria-label="Step into the world of gaming fashion with our exclusive collection of gaming t-shirts. Check out our shop to find your perfect match!"
		>
			Step into the world of gaming fashion with our exclusive collection of gaming t-shirts. Check
			out our shop to find your perfect match!
		</p>
		<button class={styles.hero__button}>
			<a href="/shop" aria-label="Shop Now">Shop Now</a>
		</button>
	</div>
</div>
