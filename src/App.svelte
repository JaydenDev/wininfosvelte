<script>
  import windowslist from "./data";
  import themelist from "./themelist";
  import Notifications from "svelte-notifications";
  let selectedTheme = "w11dark";
</script>

<div class="container {selectedTheme}">
  <h1>WinInfo by JaydenDevelopment</h1>
  <p>Dynamic WebApp with information about Windows builds.</p>
  <div class="card {selectedTheme}">
  <table>
    <tr>
      <th>Name</th>
      <th>Build</th>
      <th>Codename</th>
      <th>EOL</th>
    </tr>
    {#each windowslist as windows}
    <tr>
      <td>{windows.name}</td>
      <td>{windows.build}</td>
      <td>{windows.codename}</td>
      <td>{windows.eol}</td>
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
  }
  td, th {
    width: 100px;
    padding-bottom: 2pt;
    padding-top: 2pt;
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
