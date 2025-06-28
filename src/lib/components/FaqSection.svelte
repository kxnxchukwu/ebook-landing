<script lang="ts">
	import { Button, FaqItem } from '$components';
	import twitter from '$assets/icons/twitter.webp';
	import { faqs } from '$assets/additionalData';
	let questionExpanded = $state(-1);
	const handleQuestionClick = (index: number) => {
		questionExpanded = questionExpanded === index ? -1 : index;
	};
</script>

<section class="landing-page-section">
	<h2 class="mb-l">Frequently asked question</h2>
	<div class="faq-container">
		{#each faqs as faq, index}
			<FaqItem
				{faq}
				isExpanded={index === questionExpanded}
				onclick={() => handleQuestionClick(index)}
			/>
		{/each}
	</div>

	<div class="additional-info mt-m">
		<Button class="mt-s">Buy Now</Button>
		<p class="mt-m">Any other questions</p>
		<a href="https://x.com/kxnxchukwu" target="_blank" rel="noopener noreferrer">
			<p>Hit me up on Twitter <img src={twitter} class="twitter-icon" alt="twitter icon" /></p>
		</a>
	</div>
</section>

<style>
	.additional-info {
		display: flex;
		flex-direction: column;
		align-items: center;
		color: grey;
	}

	.twitter-icon {
		width: 16px;
		height: 16px;
	}

	.additional-info a {
		text-decoration: underline;
	}
</style>
