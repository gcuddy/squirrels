<script>
  /**
   * @type {{story: string; type: string;}}
   */
  export let story;

  /**
   * @type {boolean}
   */
  export let revealed = false;
</script>

<div class="story">
  {#if revealed}
    <p class="reveal">{story.type}</p>
  {/if}
  <p>{story.story}</p>
  <button on:click>Choose me</button>
</div>

<style>
  .reveal {
    color: green;
    font-weight: bold;
  }
  .story {
    border: 1px solid hsl(32, 64%, 42%);
    border-radius: 12px;
    padding: 12px;
    margin-top: 12px;
  }
</style>
