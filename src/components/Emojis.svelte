<script>
  import Emoji from "./Emoji.svelte";
  import { emojidata } from "./emojidata.svelte";

  let arr = [];

  setEmojis();
  function setEmojis() {
    let array = [];
    for (let i = 0; i < 3; i++) {
      array.push(randomPick(emojidata));
    }

    arr = array;
  }

  function randomPick(myArray) {
    return myArray[Math.floor(Math.random() * myArray.length)];
  }
</script>

<ul class="flex flex-row justify-center">
  {#each arr as item}
    <Emoji>{item}</Emoji>
  {/each}

</ul>
