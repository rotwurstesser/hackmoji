<script>
  export let historyItems = [];
</script>

<div class="history w-slotlarge mt-32">
  {#each historyItems as item}
    <div class="flex p-1 bg-gray-200 mb-1 rounded-lg">
      <div class="w-20 ml-1">#{item.id}</div>
      {#each item.icons as icon}
        <div class="mr-1 text-3xl">{icon}</div>
      {/each}
    </div>
  {/each}
</div>
