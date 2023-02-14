<script>
  import VideoStream from './components/VideoStream.svelte'
  let ipAddressA = localStorage.getItem('firstIPaddress')
  let ipAddressB = localStorage.getItem('secondIPaddress')
  let ping_view = ''

  import { io } from "socket.io-client";
  const socket = io("http://127.0.0.1:5001");

  // client-side
  socket.on("connect", () => {
    console.log("---connected---")
    console.log(socket.id); // x8WIv7-mJelg7on_ALbx
  });

  //ping-check
  function ping_insert(ping_value){
    if(ping_value){
      return ping_view = ping_value
    }
    else{
      return ping_view = '0'
    }
    }

  function trigger(){
    socket.emit('trigger');
  }
  
  socket.on('connect', function() { 
    socket.on('receive_ping', (msg) => { 
      ping_insert(msg)
    });
  });

  setInterval(trigger,'1000')
</script>

<main>
  <h1>Svelte Camera Viewer</h1>
  <p>{ping_view}</p>
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