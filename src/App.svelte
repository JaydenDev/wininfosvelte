<script>
  import oslist from "./data";
  import themelist from "./themelist";
  let selectedTheme = "w11dark";
</script>

<div class="container {selectedTheme}">
  <h1>OSInfo</h1>
  <p>The place to go for everything OS related</p>
  <a href="https://forms.gle/4ffTLwd8raVbgrNJ7">Submit OS</a>
  <input style="color: black;" type="text" id="searchbox" name="searchbox" list="osdatlist">
  <datalist id="osdatlist">
  {#each oslist as os}
      <option>{os.name}</option>
  {/each}
  </datalist>
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
