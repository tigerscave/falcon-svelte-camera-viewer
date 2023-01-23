<script>
  import VideoStream from './components/VideoStream.svelte'
</script>

<main>
  <h1>Svelte Camera Viewer</h1>
  <VideoStream />
  <VideoStream ipAddress="192.168.1.10" />
  <!-- <CameraB /> -->
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
