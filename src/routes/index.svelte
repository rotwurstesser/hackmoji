<script>
  import { emojidata } from "../components/emojidata.svelte";
  import Emojis from "../components/Emojis.svelte";
  import History from "../components/History.svelte";

  $: slotAmount = 3;

  let emojis = [];
  let historyItems = [];

  function setEmojis() {
    let array = [];
    for (let i = 0; i < slotAmount; i++) {
      array.push(randomPick(emojidata));
    }
    emojis = array;

    let _historyItems = { icons: array, id: historyItems.length + 1 };
    historyItems = [_historyItems, ...historyItems];
  }

  function randomPick(myArray) {
    return myArray[Math.floor(Math.random() * myArray.length)];
  }
</script>

<svelte:head>
  <title>Sapper project template</title>
</svelte:head>
<div class="flex flex-col">

  <h1 class="font-raleway mt-10 pb-10 px-10 self-center text-5xl text-center">
    Hackmoji! The perfect Ideation Companion for you
  </h1>
  <label
    class="flex flex-col font-raleway self-center text-base text-center mb-12"
    for="amountOfSlots">
    <span>Amount of slots in next render</span>
    <input
      type="number"
      class="bg-gray-200 rounded-lg p-3"
      bind:value={slotAmount} />
  </label>

  <Emojis {emojis} />

  <button
    class="bg-black font-raleway mt-16 px-12 py-6 rounded-lg self-center
    text-4xl text-white w-auto"
    on:click={setEmojis}>
    Let's Roll
  </button>

  <div class="flex flex-row justify-center">
    <History {historyItems} />
  </div>
</div>
