<script>
  let title = "World";
  import Game from "../lib/Game.svelte";
  import Squirrels from "../lib/Squirrels.svelte";
  import Wordcloud from "../lib/wordcloud.svelte";
  $: secondTitle = title + " Squirrels";

  import stories from "$lib/stories.json";
</script>


<svelte:head>
    <title>🐿️ Squirrel Stories</title>
</svelte:head>
<main>
  <div class="header">
    <h1>🐿️ Squirrel Stories 🐿️</h1>
    <span
      >Real or fake? (data from <a href="https://www.thesquirrelcensus.com/"
        >The Squirrel Census</a
      >)</span
    >
  </div>
  <div class="wordcloud">
    <Wordcloud />
  </div>

  <Game data={stories} />
</main>

<style>
  .header {
    margin-bottom: 20px;
  }

  .wordcloud {
    transform: scale(0.5);
    margin: -148px;
  }

  main {
    max-width: 45rem;
    margin-left: auto;
    margin-right: auto;
    padding-left: 1rem;
    padding-right: 1rem;
  }
</style>
