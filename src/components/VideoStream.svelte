<script>
  export let ipAddress = ''
  let isEditing = !ipAddress

  function toggleEditing() {
    isEditing = !isEditing
  }
</script>

<div>
  {#if isEditing}
    <input type="input" bind:value={ipAddress} />
    <input type="button" value="Save" on:click={toggleEditing} />
  {:else}
    <div style="display: flex">
      <p style="border: solid 1px black; padding: 0.8rem; margin: 0;">
        {ipAddress}
      </p>
      <button on:click={toggleEditing}>Edit</button>
    </div>
  {/if}

  <br />
  <!-- svelte-ignore a11y-missing-attribute -->
  <iframe
    name="ifr1"
    id="ifr1"
    src="http://{ipAddress}:7011/ImageViewer?Mode=Motion&Resolution=320x240&Quality=Standard&Interval=10"
    width="800"
    height="500"
  />
  <br />
</div>

<style>
</style>
