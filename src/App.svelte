<script>
  import windowslist from "./data";
  import themelist from "./themelist";
  import linuxlist from "./data";
  import Notifications from "svelte-notifications";
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
    {#each windowslist as windows}
    <tr>
      <!-- svelte-ignore a11y-missing-attribute -->
      <td><img src={windows.logo} length=40 width=40></td>
      <td>{windows.name}</td>
      <td>{windows.type}</td>
      <td>{windows.build}</td>
      <td>{windows.rel}</td>
      <td>{windows.codename}</td>
      <td>{windows.eol}</td>
      <td>{windows.platform}</td>
    </tr>
    {/each}
  </table>
  </div>
</div>
<label for="theme">Choose a theme: </label>
<select name="theme" id="theme" bind:value={selectedTheme}>
  {#each themelist as theme}
    <option value={theme}>{theme}</option>
  {/each}
</select>

<style>
  /* button {
    border-radius: 5pt;
  } */
  
  table {
    table-layout: fixed;
    border-collapse: collapse;
    border-spacing: 0;
    width: 85%;
  }
  td, th {
    width: 100px;
    padding-bottom: 4pt;
    padding-top: 4pt;
    text-align: center;
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
    width: 85%;
    background-color: white;
    border-radius: 5pt;
    color: black;
    padding: 1pt;
  }

</style>
