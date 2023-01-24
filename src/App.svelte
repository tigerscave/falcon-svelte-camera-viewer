<script>
  import VideoStream from './components/VideoStream.svelte'
  let ipAddressA = localStorage.getItem('firstIPaddress')
  let ipAddressB = localStorage.getItem('secondIPaddress')

</script>

<main>
  <h1>Svelte Camera Viewer</h1>
<VideoStream ipAddress={ipAddressA} stragekey='firstIPaddress'/>
<VideoStream ipAddress={ipAddressB} stragekey='secondIPaddress'/>

</main>

<style>
  h1{
    margin: 0;
    color: white;
  }
  main{
    background-color: #144998;
  }
</style>