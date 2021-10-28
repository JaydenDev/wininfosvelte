<script>
  import windowslist from "./data";
  import themelist from "./themelist";
  import Notifications from "svelte-notifications";
  import Child from "./child.svelte";
  let selectedTheme = "w11dark";
</script>

<div class="container {selectedTheme}">
  <div class="notification">
    <Notifications>
      <Child {selectedTheme}/>
    </Notifications>
  </div>
  
  <label for="theme">Choose a theme: </label>
  <select name="theme" id="theme" bind:value={selectedTheme}>
    {#each themelist as theme}
      <option value={theme}>{theme}</option>
    {/each}
  </select>
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
  </table> 
  {/each}
  </div>
</div>

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
  }
  
  pre {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
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
  
  .card {
    font-size: 10pt;
    height: 50%;
    width: 35%;
    background-color: white;
    color: black;
    padding: 1pt;
  }

</style>
