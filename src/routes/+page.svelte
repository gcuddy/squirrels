<script>
  let title = "World";
  import Game from "../lib/Game.svelte";
  import Squirrels from "../lib/Squirrels.svelte";
  import Wordcloud from "../lib/wordcloud.svelte";
  $: secondTitle = title + " Squirrels";

  import stories from '$lib/stories.json';
</script>

<div class="header">
  <h1>Squirrel Stories</h1>
  <div>Real or fake?</div>
</div>
<div class="wordcloud">
  <Wordcloud />
</div>

<Game
  data={stories}
/>

<style>
  .header {
    margin-bottom: 20px;
  }

  .wordcloud {
    transform: scale(0.5);
    margin: -148px;
  }
</style>
