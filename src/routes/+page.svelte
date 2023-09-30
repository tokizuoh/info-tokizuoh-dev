<script>
    import Icon from "./Icon.svelte"
    import Posts from "./Posts.svelte"
    import Links from "./Links.svelte"
    import Works from "./Works.svelte"
    import Copyright from "./Copyright.svelte"
    
    const title = "tokizuoh"
    const description = `
        I'm working as a software engineer in Japan.
    `
</script>

<title>{title}</title>
<h1>tokizo</h1>
<Icon />

<Posts />
<Links />
<Works />
<Copyright />

<style>
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP&display=swap');

:global(body) {
    font-family: 'Noto Sans JP', sans-serif;

    background-color: rgb(25, 28, 35); 
    color: #EEEEEE;

    width: 800px;
    margin-top: 80px;
    margin-right: auto;
    margin-left: auto;
    margin-bottom: 100px;

    @media screen and (max-width: 959px) {
        margin-left: 24px;
        margin-right: 24px;
        width: auto;
    }
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
    text-decoration:underline;
}

:global(a:hover) {
    color: white;
}
p {
    color: #BBBBBB;
}
</style>
