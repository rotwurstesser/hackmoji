<script>
  import { emojidata } from "../components/emojidata.svelte";
  import Emojis from "../components/Emojis.svelte";
  import History from "../components/History.svelte";
  import ConfettiGenerator from "confetti-js";

  $: slotAmount = 3;

  let emojis = ["", "", ""];
  let historyItems = [];

  function setEmojis() {
    const width =
      window.innerWidth ||
      document.documentElement.clientWidth ||
      document.body.clientWidth;

    const height =
      window.innerHeight ||
      document.documentElement.clientHeight ||
      document.body.clientHeight;

    var confettiSettings = {
      target: "my-canvas",
      width: width,
      height: height
    };
    var confetti = new ConfettiGenerator(confettiSettings);
    confetti.render();
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
  <title>Hackmoji</title>
</svelte:head>
<canvas class="absolute z-background opacity-50" id="my-canvas" />
<div class="flex flex-col">

  <h1 class="font-raleway mt-10 px-10 self-center text-4xl text-center">
    Hackmoji!
  </h1>
  <h2 class="font-raleway pb-10 px-10 self-center text-2xl text-center">
    The perfect Ideation Companion for you
  </h2>

  <Emojis {emojis} />
  <label
    class="flex flex-col font-raleway self-center text-base text-center mb-12
    mt-4"
    for="amountOfSlots">
    <span>Amount of slots in next render</span>
    <input
      type="number"
      class="bg-gray-200 rounded-lg p-3"
      bind:value={slotAmount} />
  </label>
  <button
    class="bg-black font-raleway px-12 py-6 rounded-lg self-center text-4xl
    text-white w-auto"
    on:click={setEmojis}>
    Let's Roll
  </button>

  <div class="flex flex-row justify-center">
    <History {historyItems} />
  </div>
</div>
