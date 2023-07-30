<script>
	import { onMount } from "svelte";

    onMount(() => {
        fetchItems();
    });

    async function fetchItems() {
        const parser = new DOMParser();
        const res = await fetch("https://tokizuoh.hatenablog.com/rss?size=5");
        const data = await res.text();
        const obj = await parser.parseFromString(data, "text/xml");
        const items = obj.querySelectorAll("item");
        const links = await Promise.all(Array.from(items).map(async (item) => {
            const itemDom = parser.parseFromString(item.innerHTML, "text/html");
            const title = itemDom.querySelector("title").textContent;
            const url = itemDom.querySelector("body").firstChild.nodeValue;
            return [title, url];
        }));
        return links;
    }
</script>

<h2>Posts</h2>
{#await fetchItems()}
    <p>ロード中</p>
{:then links}
    <ul>
        {#each links as l}
            <li>
                <a href="{l[1]}" target="_blank" rel="noopener noreferrer">
                    {l[0]}
                </a>
            </li>
        {/each}
    </ul>
{/await}
