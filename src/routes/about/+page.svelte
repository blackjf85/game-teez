<script>
	import { onMount } from 'svelte';
	import styles from '../../styles/pages/About.module.css';
	let about;

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
			about.classList.add(styles['about--webp']);
		}
	});
</script>

<main>
	<div class={`${styles.about}`} bind:this={about}>
		<div class={styles.about__content}>
			<h1 class={styles.about__heading}>
				About <span class={styles.about__headingAccent}>Us</span>
			</h1>
			<p class={styles.about__text}>
				Welcome to GameTeez! We are an online store specializing in stylish t-shirts for gamers. Our
				goal is to provide high-quality clothing that allows you to express your love for gaming.
			</p>
			<p class={styles.about__text}>
				At GameTeez, we are passionate about gaming. As gamers ourselves, we know how important it
				is to have comfortable and stylish clothing that reflects our love for gaming. That's why we
				offer a range of t-shirts featuring unique designs that will help you stand out from the
				crowd. Thank you for choosing GameTeez. We are excited to be part of your gaming journey and
				to help you express your love for gaming through our stylish t-shirts.
			</p>
			<button class={styles.about__button}>
				<a href="/shop">Shop Now</a>
			</button>
		</div>
	</div>
</main>
