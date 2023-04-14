<script>
	//components
	import Header from '../components/Header.svelte';
	import Footer from '../components/Footer.svelte';

	//analytics
	import { dev } from '$app/environment';
	import { inject } from '@vercel/analytics';
	inject({ mode: dev ? 'development' : 'production' });
</script>

<div class="app">
	<Header />
	<main>
		<slot />
	</main>
	<Footer />
</div>
