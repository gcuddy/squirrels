<script>
  import { onMount } from "svelte";

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

  //   onMount(() => {
  //     stories = getStories();
  //   })
</script>

<div class="container">
  <div
    on:click={() => {
      if (stories[0].type === "robot") {
        alert("You got it right!");
      } else {
        alert("You got it wrong!");
      }
    }}
  >
    {stories[0].story}
  </div>
  <div
    on:click={() => {
      if (stories[1].type === "robot") {
        alert("You got it right!");
      } else {
        alert("You got it wrong!");
      }
    }}
  >
    {stories[1].story}
  </div>
</div>

<style>
  .container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1rem;
  }
</style>
