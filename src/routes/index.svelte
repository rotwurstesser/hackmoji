<script>
  import Emojis from "../components/Emojis.svelte";
</script>

<svelte:head>
  <title>Sapper project template</title>
</svelte:head>
<div class="flex flex-col">

  <h1 class="self-center mt-10 pb-10 text-5xl font-raleway">
    Hackmoji! The perfect Ideation Companion for you
  </h1>

  <Emojis />

  <button
    class="bg-black font-raleway mt-16 px-12 py-6 rounded-lg self-center
    text-4xl text-white w-1/6">
    Let's Roll
  </button>
</div>
