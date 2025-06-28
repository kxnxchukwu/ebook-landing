<script lang="ts">
	import authorPic from '$assets/authorPic.jpeg';
</script>

<section class="landing-page-section">
	<h2 class="mb-l">About the Author</h2>
	<div class="author-container">
		<div class="author-text">
			<p class="mb-s">
				Hi, I'm Kenechukwu Ajufo, a digital nomad who has lived in Spain for over 5 years. I created
				this ebook to help others avoid the common pitfalls I faced when moving abroad.
			</p>
			<p>
				My journey has been filled with challenges and triumphs, and I want to share my experiences
				to make your move smoother and more enjoyable.
			</p>
		</div>
		<img src={authorPic} alt="Author Kenechukwu Ajufo" />
	</div>
</section>

<style>
	.author-container {
		display: flex;
		justify-content: space-between;
	}

	.author-container img {
		width: 40%;
		border: 2px solid black;
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.5);
	}

	.author-text {
		width: 55%;
	}
</style>
