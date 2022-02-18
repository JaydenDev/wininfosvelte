<script>
  import oslist from "./data";
  import themelist from "./themelist";
  let selectedTheme = "w11dark";
  
  //function itemSel() {
    //var item = document.getElementById("searchbox").value;
    //text.search(item);
  //} sad :(
</script>
  <p>This is the beta version of WinInfo, expect to encounter issues</p><a href="https://osinfo.vercel.app">Stable Version</a>
  <hr>
  <div style="background-color: crimson; width: 100vw; width: 5vh; color: white;">
    <h1> Warning to MacOS Catalina Users </h1>
    <p> MacOS Catalina hits EOL in 9 months </p>
 </div>
  <h1>OSInfo</h1>
  <p>The place to go for everything OS related</p>
  <br>
  <!-- webdev03/god286, I can't get any of this to work, please fix sad D:
  <input placeholder="Search OS" style="width: 50vw; color: black; border-radius: 5pt; outline: none;" type="text" id="searchbox" name="searchbox" list="osdatlist"> <button onClick="itemSel()" style="width: 50vw">Search</button>
  <datalist id="osdatlist">
  {#each oslist as os}
      <option>{os.name}</option>
  {/each}
  </datalist> -->
  <table border=1 frame=void rules=rows>
    <tr>
      <th> </th>
      <th>Name</th>
      <th>Type/Channel</th>
      <th>Build</th>
      <th>Released</th>
      <th>Codename</th>
      <th>EOL</th>
      <th>Platform</th>
      <th>Download</th>
    </tr>
    {#each oslist as os}
    <tr>
        <!-- svelte-ignore a11y-missing-attribute -->
        <td><img src={os.logo} length=40 width=40></td>
        <td>{os.name}</td>
        <td>{os.type}</td>
        <td>{os.build}</td>
        <td>{os.rel}</td>
        <td>{os.codename}</td>
        <td>{os.eol}</td>
        <td>{os.platform}</td>
        <td><a href={os.download}>Download</a>
      </tr>
    {/each}
  </table>
<!-- <label for="theme">Choose a theme: </label>
<select name="theme" id="theme" bind:value={selectedTheme}>
  {#each themelist as theme}
    <option value={theme}>{theme}</option>
  {/each}
</select> -->
<style>
  /* button {
    border-radius: 5pt;
  } */
  body {
    background-color: #0D1117;
  }
  table {
    table-layout: fixed;
    border-collapse: collapse;
    border-spacing: 0;
    width: fit-content;
  }
  td, th {
    width: 100px;
    padding-bottom: 4pt;
    padding-top: 4pt;
  }
  td:hover {
    transform: scale(1.1);
  }
  th:hover {
    transform: scale(1.1);
  }
  * {
    color: white;
  }
  
  .container {
    width: 100%;
    min-height: 100%;
    padding: none;
    margin: none;
  }
  
  .header {
    text-align: center;
    font-size: 12pt;
    padding-bottom: 2pt;
    width: 35%;
    border-radius: 5pt;
  }
  .card {
    font-size: 12pt;
    height: fit-content;
    width: fit-content;
    background-color: white;
    border-radius: 5pt;
    color: black;
    padding: 1pt;
  }
</style>
