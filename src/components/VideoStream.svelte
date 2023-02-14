<script>
  
  export let ipAddress = ''
  export let stragekey = ''
  
  let isEditing = !ipAddress

  function toggleEditing() {
    isEditing = !isEditing
    localStorage.setItem(stragekey,ipAddress);
    onlineJudge();
  }

  // プリセット保存した際の画面遷移を防止するため、ページをリロードする関数を追加
  function reloadAfter100ms(){
    setTimeout(() => {
    location.reload()
    }, 100)
  }

</script>
<a href="http://{ipAddress}:7011/cgi-bin/directctrl?zoom=2" class="zoom-btn-ip"><img src="img/zoom.png" alt="zoom-btn" class="zoom-png"></a>
<br>
<a href="http://{ipAddress}:7011/cgi-bin/directctrl?zoom=-2" class="zoom-out-btn"><img src="img/zoomout.png" alt="zoom-out-btn" class="zoom-out-png"></a>
<p>プリセット</p>
<a href="http://nwcadmin:Passwd34@{ipAddress}:7011/cgi-bin/camposiset?presetset=1" on:click={reloadAfter100ms} class="preset-btn">①保存</a>
<a href="http://nwcadmin:Passwd34@{ipAddress}:7011/cgi-bin/camposiset?presetset=2" on:click={reloadAfter100ms} class="preset-btn">②保存</a>
<a href="http://nwcadmin:Passwd34@{ipAddress}:7011/cgi-bin/camposiset?presetset=3" on:click={reloadAfter100ms} class="preset-btn">③保存</a>

<a href="http://{ipAddress}:7011/cgi-bin/camctrl?preset=1" class="btn">プリセット1移動</a>
<a href="http://{ipAddress}:7011/cgi-bin/camctrl?preset=2" class="btn">プリセット2移動</a>
<a href="http://{ipAddress}:7011/cgi-bin/camctrl?preset=3" class="btn">プリセット3移動</a>

<p class="ipaddress-text">IPアドレス</p>

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
  <p class="conecting-txt">{name}</p>
  <!-- svelte-ignore a11y-missing-attribute -->
  <iframe
    name="ifr1"
    id="ifr1"
    src="http://{ipAddress}:7011/ImageViewer?Mode=Motion&Resolution=500x800&Quality=Standard&Interval=10"
    width="800"
    height="500"
  />
  <br />
</div>


<style>
  .ipaddress-text{
    color: white;
    margin: 0;
    font-size: 1rem;
    padding: 1rem;
  }
  .container {
    font-size: 1.2rem;
    padding: 1rem;
  }
  .input-ip{
    border: solid 1px black;
    height: 25px;
    width: 130px;
    font-size: 80%;
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
    border: 1px dashed white;
    height: 25px;
    width: 130px;
    font-size: 80%;
  }
  .zoom-btn-ip{
    color: white;
    width: 10%;
    height: auto;
  }
  .zoom-out-btn{
    color: white;
  }
  .zoom-png{
    width: 1.5%;
    height: auto;
  }
  .zoom-out-png{
    width: 1.5%;
    height: auto;
  }
  .preset-btn {
    display: block;
    text-align: center;
    text-decoration: none;
    width: 120px;
    margin: auto;
    padding: 0.5rem 0rem;
    font-weight: bold;
    border: 2px solid #27acd9;
    color: #27acd9;
    border-radius: 100vh;
    transition: 0.5s;
  }
  .preset-btn:hover {
    color: #fff;
    background: #27acd9;
  }
  .conecting-txt{
    color: white;
  }
</style>
