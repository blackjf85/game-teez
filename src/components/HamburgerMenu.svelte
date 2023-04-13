<script>
	import styles from '../styles/components/HamburgerMenu.module.css';
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();
	export let showMenu = false;

	function closeMenu() {
		dispatch('close');
	}
</script>

{#if showMenu}
	<div
		on:click={closeMenu}
		on:keydown={(e) => e.key === 'Enter' && closeMenu()}
		class={styles.menu}
		role="button"
		tabindex="0"
	>
		<button class={styles.menu__close} on:click={closeMenu}>X</button>
		<ul class={styles.menu__list}>
			<li class={styles.menu__item}>
				<button
					class={styles.menu__link}
					on:click={() => {
						closeMenu();
						location.href = '/';
					}}>Home</button
				>
			</li>
			<li class={styles.menu__item}>
				<button
					class={styles.menu__link}
					on:click={() => {
						closeMenu();
						location.href = '/about';
					}}>About</button
				>
			</li>
			<li class={styles.menu__item}>
				<button
					class={styles.menu__link}
					on:click={() => {
						closeMenu();
						location.href = '/contact';
					}}>Contact</button
				>
			</li>
			<li class={styles.menu__item}>
				<button
					class={styles.menu__link}
					on:click={() => {
						closeMenu();
						location.href = '/shop';
					}}>Shop</button
				>
			</li>
		</ul>
	</div>
{/if}
