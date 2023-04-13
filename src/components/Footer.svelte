<script>
	import { db } from '../lib/firebase/firebase.js';
	import { collection, addDoc, query, where, getDocs } from 'firebase/firestore';
	import styles from '../styles/components/Footer.module.css';
	import Logo from '../lib/images/Game_Teez_logo_square--transparent.svg';

	let email = '';
	let submitted = false;
	let message = '';

	function validateEmail(input) {
		const regex = /\S+@\S+\.\S+/;
		return regex.test(input);
	}

	async function handleSubmit() {
		if (!validateEmail(email)) {
			message =
				"It looks like that wasn't a valid email, please provide a valid email address to subscribe to our mailing list for exclusive offers and discounts!";
			return;
		}

		const subscribersCollection = collection(db, 'subscribers');
		const q = query(subscribersCollection, where('email', '==', email));
		const querySnapshot = await getDocs(q);

		if (querySnapshot.size > 0) {
			message = 'It looks like you are already subscribed, thank you!';
			submitted = true;
			return;
		}

		try {
			await addDoc(subscribersCollection, { email });
			message = 'Thank you for subscribing!';
			submitted = true;
		} catch (e) {
			console.error('Error adding document: ', e);
		}
	}
</script>

<footer class={styles.footer}>
	{#if message}
		<p class={styles.subscribedMessage}>
			{message}
		</p>
	{:else}
		<div class={styles.mailingList} aria-labelledby="mailingListLabel">
			<p id="mailingListLabel" class={styles.mailingList__invitation}>
				Join our mailing list for exclusive updates and offers!
			</p>
			<div class={styles.mailingList__form}>
				<input
					class={styles.mailingList__input}
					type="email"
					placeholder="Enter your email"
					bind:value={email}
					aria-label="Enter your email address"
				/>
				<button
					class={`${styles.mailingList__button} ${styles.mailingList__input}`}
					on:click={handleSubmit}
					aria-label="Submit your email address"
				>
					Submit
				</button>
			</div>
		</div>
	{/if}
	<div class={styles.logo} aria-label="GameTeez Logo">
		<a href="/">
			<img class={styles.logo__image} src={Logo} alt="GameTeez Logo" />
		</a>
	</div>
	<p class={styles.copyRight}>
		&copy; <em>Copyright GameTeez 2023</em>
	</p>
</footer>
