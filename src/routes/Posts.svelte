<script context="module">
	import latest_posts from './../data/latest_posts.json';

	const links = latest_posts.map((item) => {
		const title = item.title;
		const url = item.url;
		const pubDateStr = new Date(item.publishedAt).toLocaleDateString('ja-JP', {
			year: 'numeric',
			month: '2-digit',
			day: '2-digit'
		});
		return [title, url, pubDateStr];
	});
</script>

<h2>Posts</h2>
{#if links}
	<ul>
		{#each links as l}
			<li>
				<div>
					<a href={l[1]}>
						{l[0]}
					</a>
					<div class="pub-date">({l[2]})</div>
				</div>
			</li>
		{/each}
	</ul>
{:else}
	<p>Loading...</p>
{/if}

<style>
	li div {
		display: inline;
	}

	.pub-date {
		color: #888888;
		margin-left: 4px;
		font-size: 95%;
	}
</style>
