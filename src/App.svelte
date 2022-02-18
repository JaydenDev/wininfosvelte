<script>
  import oslist from "./data";
  import themelist from "./themelist";
  let selectedTheme = "w11dark";
</script>

<div class="container {selectedTheme}">
  <h1>OSInfo by JaydenDevelopment</h1>
  <p>Dynamic WebApp with information about OS builds.</p>
  <div class="card {selectedTheme}">
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
    </tr>
    {/each}
  </table>
  </div>
</div>
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
    height: 50%;
    width: 65%;
    background-color: white;
    border-radius: 5pt;
    color: black;
    padding: 1pt;
  }
  a:hover {
    color: #0D1117;
  }
</style>
