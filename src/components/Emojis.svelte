<script>
  import Emoji from "./Emoji.svelte";

  export let emojis = [];
  console.log("items", emojis);
</script>

<ul class="flex flex-row justify-center">
  {#each emojis as item}
    <Emoji>{item}</Emoji>
  {/each}

</ul>
