<script>
    import Icon from "./Icon.svelte";
    import Links from "./Links.svelte"
    import Copyright from "./Copyright.svelte";
    
    const description = `
        I'm a software developer in Japan.
    `
</script>

<h1>tokizuoh</h1>
<Icon />

<h2>About</h2>
<p>{description}</p>

<h2>Posts</h2>
<ul>
    <li>ダジャレで戦うDMM英会話</li>
    <li>RustでScrapboxのハッシュタグに紐づくページ数を集計するツールを作った</li>
    <li>2023年6月を振り返る</li>
</ul>

<Links />
<Copyright />

<style>
@import url(http://fonts.googleapis.com/earlyaccess/notosansjp.css);

:global(body) {
    background-color: rgb(25, 28, 35); 
    color: #EEEEEE;

    width: 800px;
    margin-top: 80px;
    margin-right: auto;
    margin-left: auto;
    margin-bottom: 100px;

    font-family: 'Noto Sans JP', sans-serif;
}

:global(h2) {
    margin-top: 60px;
    margin-bottom: 0px;
}

:global(li) {
    margin-bottom: 2px;
    color: #BBBBBB;
}

:global(a) {
    color: #BBBBBB;
    text-decoration:underline 
}

:global(a:hover) {
    color: white;
}
p {
    color: #BBBBBB;
}
</style>
