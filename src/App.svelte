<script>
  let ipaddress = ''
  let ipaddress2 = ''
</script>

<main>
  <input bind:value={ipaddress} />
  <input
    type="button"
    value="reload"
    onclick="frames['ifr1'].location.reload();"
  />
  <br />
  <!-- svelte-ignore a11y-missing-attribute -->
  <iframe
    name="ifr1"
    id="ifr1"
    src="http://{ipaddress}:7011/ImageViewer?Mode=Motion&Resolution=320x240&Quality=Standard&Interval=10"
    width="800"
    height="500"
  />
  <br />
  <br />
  <!-- svelte-ignore a11y-missing-attribute -->
  <iframe
    name="ifr2"
    id="ifr2"
    src="http://{ipaddress2}:7011/ImageViewer?Mode=Motion&Resolution=320x240&Quality=Standard&Interval=10"
    width="800"
    height="500"
  />
  <input bind:value={ipaddress2} />
  <input
    type="button"
    value="reload"
    onclick="frames['ifr2'].location.reload();"
  />
</main>

<style>
</style>
