<script context="module">
    async function load() {
        const cacheLife = 3600;

        var cachedData = localStorage.getItem('posts');
        if (cachedData) {
            cachedData = JSON.parse(cachedData);
            var expired = parseInt(Date.now() / 1000) - cachedData.cachedTime > cacheLife
        }

        if (cachedData && !expired) {
            return cachedData.links;
        } else {
            const parser = new DOMParser();
            const res = await fetch("https://tokizuoh.hatenablog.com/rss?size=5");
            const data = await res.text();
            const obj = await parser.parseFromString(data, "text/xml");
            const items = obj.querySelectorAll("item");
            const links = await Promise.all(Array.from(items).map(async (item) => {
                const itemDom = parser.parseFromString(item.innerHTML, "text/html");
                const title = itemDom.querySelector("title").textContent;
                const url = itemDom.querySelector("body").firstChild.nodeValue;
                const pubDate = itemDom.querySelector("pubdate").firstChild.nodeValue;
                const pubDateStr = new Date(pubDate).toLocaleDateString("ja-JP", {year: "numeric",month: "2-digit", day: "2-digit"})
                return [title, url, pubDateStr];
            }));
            var cache = {links: links, cachedTime: parseInt(Date.now() / 1000)};
            localStorage.setItem('posts', JSON.stringify(cache));
            return links;
        }
    }
</script>

<h2>Posts</h2>
{#await load()}
{:then links}
    <ul>
        {#each links as l}
            <li>
                <div>
                    <a href="{l[1]}">
                        {l[0]}
                    </a>
                    <div class="pub-date">({l[2]})</div>
                </div>
            </li>
        {/each}
    </ul>
{/await}

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
