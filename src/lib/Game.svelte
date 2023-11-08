<script>
  import { onMount } from "svelte";
  import Story from "./Story.svelte";

  /**
   * @type {{humans: string[]; robots: string[]}}
   */
  export let data;

  function getStories() {
    const humanIdx = Math.floor(Math.random() * data.humans.length);
    const humanStory = data.humans[humanIdx];

    const robotIdx = Math.floor(Math.random() * data.robots.length);
    const robotStory = data.robots[robotIdx];

    const robotLeft = Math.random() > 0.5;

    if (robotLeft) {
      return [
        {
          story: robotStory,
          type: "robot",
        },
        {
          story: humanStory,
          type: "human",
        },
      ];
    } else {
      return [
        {
          story: humanStory,
          type: "human",
        },
        {
          story: robotStory,
          type: "robot",
        },
      ];
    }
  }

  let stories = getStories();
  let chosen = false;

  onMount(() => {
    chosen = false;
  });
</script>

<!-- TODO: use server actions so json isn't leaked to client -->

<h2>Choose the <em>fake</em> squirrel story:</h2>
<button
  on:click={() => {
    chosen = false;
    stories = getStories();
  }}>Next</button
>
<div class="container">
  {#each stories as story}
    <Story
      revealed={chosen}
      on:click={() => {
        chosen = true;
        if (story.type === "robot") {
          alert("Correct! This story was written by AI.");
        } else {
          alert("Nope! This story was written by a squirrel census taker.");
        }
      }}
      {story}
    />
  {/each}
</div>

<style>
  .container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }
</style>
