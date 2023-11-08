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

<div>
  <p>{story.story}</p>
  <button on:click>Choose me</button>
  {#if revealed}
    <p class="reveal">{story.type}</p>
  {/if}
</div>

<style>
    .reveal {
        color: green;
        font-weight: bold;
    }
</style>

