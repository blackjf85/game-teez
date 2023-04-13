<script>
	import styles from '../styles/components/Hero.module.css';
	import BackgroundPng from '../lib/images/hero_image.png';
	import BackgroundWebp from '../lib/images/hero_image.webp';
</script>

<div class={styles.hero}>
	<picture>
		<source srcset={BackgroundWebp} type="image/webp" />
		<img src={BackgroundPng} alt="Hero background" class={styles.hero__img} />
	</picture>
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
