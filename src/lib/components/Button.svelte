<script lang="ts">
	import { loadStripe } from '@stripe/stripe-js';
	import { PUBLIC_STRIPE_KEY } from '$env/static/public';
	import { goto } from '$app/navigation';
	let { children, ...props } = $props();

	const onclick = async () => {
		try {
			const stripe = await loadStripe(PUBLIC_STRIPE_KEY);

			if (!stripe) {
				console.error('Stripe failed to load');
				return;
			}

			const response = await fetch('/api/checkout', {
				method: 'POST',
				headers: {
					'Content-Type': 'application/json'
				}
			});

			if (!response.ok) {
				console.error('Failed to create checkout session');
				return;
			}

			const { sessionId } = await response.json();

			await stripe.redirectToCheckout({
				sessionId
			});
		} catch (error) {
			goto('/checkout/failure');
		}
	};
</script>

<button {...props} {onclick}>{@render children()}</button>

<style>
	button {
		background-color: black;
		color: white;
		padding: 20px 24px;
		font-weight: normal;
		font-size: 22px;
		text-transform: uppercase;
		transition: all 0.3s ease;
		border: 1px solid white;
	}

	button:hover {
		background-color: white;
		color: black;
	}
</style>
