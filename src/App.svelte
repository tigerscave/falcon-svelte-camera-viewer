<script>
  import VideoStream from './components/VideoStream.svelte'
  import { io } from "socket.io-client";
  const socket = io("http://127.0.0.1:5001");
  let ipAddressA = localStorage.getItem('firstIPaddress')
  let ipAddressB = localStorage.getItem('secondIPaddress')
  let pingResultText = "Not Connected"

  function pingCheck(){
    socket.emit('ask_ping');
  }
  
  socket.on('connect', function() { 
    socket.on('receive_ping', (value) => { 
      pingResultText = value ? 'Online' : 'Offline'
    });
  });

  setInterval(pingCheck,1000)
</script>

<main>
  <h1>Svelte Camera Viewer</h1>
  <p>{pingResultText}</p>
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