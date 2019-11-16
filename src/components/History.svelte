<script>
  import copy from "copy-to-clipboard";
  function copyStuff(event) {
    // big oof here, the passing didnt work in the time i wanted to make it work
    let stuffToCopy = event.currentTarget.parentElement.querySelector(
      ".emojientry"
    ).innerText;
    if (typeof stuffToCopy === "string") {
      stuffToCopy.replace(",", "");
    }
    copy(stuffToCopy);
  }
  export let historyItems = [];
</script>

<div class="history w-slotlarge mt-32">
  {#each historyItems as item}
    <div
      class="flex p-1 bg-gray-200 mb-1 rounded-lg justify-between items-center">
      <div class="flex">
        <div class="mx-4 flex items-center">#{item.id}</div>
        <div class="emojientry flex">
          {#each item.icons as icon}
            <div class="mr-1 text-3xl">{icon}</div>
          {/each}
        </div>
      </div>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        on:click={copyStuff}>
        <path
          d="M10 8h-2v2h-2v-4h4v2zm8 16v-2h-6v2h6zm2-16h2v2h2v-4h-4v2zm2
          12v2h-2v2h4v-4h-2zm-12 2h-2v-2h-2v4h4v-2zm14-10h-2v6h2v-6zm-16
          6v-6h-2v4h-4v-14h14v4h-4v2h6v-8h-18v18h8z" />
      </svg>
    </div>
  {/each}
</div>
