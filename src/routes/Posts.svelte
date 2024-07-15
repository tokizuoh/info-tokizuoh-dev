<script>
	import latest_posts from '../data/latest_posts.json';

	const links = latest_posts.map((item) => {
		const title = item.title;
		const url = item.url;
		const source = item.source;
		const pubDateStr = new Date(item.publishedAt).toLocaleDateString('ja-JP', {
			year: 'numeric',
			month: '2-digit',
			day: '2-digit'
		});

		let sourceDisplay;
		switch (source) {
			case 'zenn':
				sourceDisplay = 'Zenn';
				break;
			case 'hatena':
				sourceDisplay = 'Hatena Blog';
				break;
			default:
				sourceDisplay = 'Unknown';
				break;
		}

		return { title, url, source, sourceDisplay, pubDateStr };
	});
</script>

<h2>Posts</h2>
{#if links.length > 0}
	<ul>
		{#each links as link}
			<li class="post-item">
				<a href={link.url} class="title">{link.title}</a>
				<div class="meta">
					<span class="source-badge {link.source}">{link.sourceDisplay}</span>
					<span class="pub-date">{link.pubDateStr}</span>
				</div>
			</li>
		{/each}
	</ul>
{:else}
	<p>Loading...</p>
{/if}

<style>
	.meta {
		display: inline;
		font-size: 0.85em;
		color: #888888;
		margin-left: 8px;
	}

	.pub-date {
		margin-left: 4px;
	}
</style>
