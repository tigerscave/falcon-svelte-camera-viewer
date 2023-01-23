<script>
  export let ipAddress = ''
  let isEditing = !ipAddress

  function toggleEditing() {

    isEditing = !isEditing
  }
</script>

<p class="IPaddressTEXT">IPアドレス</p>

<div class="container">
  {#if isEditing}
    <div class="ip-input-box">
      <input class="input-ip" type="input" bind:value={ipAddress} />
      <input class="input-btn"  type="button" value="保存" on:click={toggleEditing} />
    </div>
  {:else}
    <div class="ip-add-box" >
      <p class="show-ip" >
        {ipAddress}
      </p>
      <button class="input-btn" on:click={toggleEditing}>編集</button>
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
  .IPaddressTEXT{
    color: white;
    margin: 0;
    font-size: 1rem;
    padding: 1rem;
  }
  .container {
    font-size: 1.2rem;
    padding: 1rem;
  }
  .input-ip {
    border: solid 1px black;
  }
  .input-btn {
    padding: 0 1rem;
    margin-left: 1rem;
  }

  .ip-add-box {
    display: flex;
  }

  .show-ip {
    margin: 0;
    color: white;
  }
  
</style>