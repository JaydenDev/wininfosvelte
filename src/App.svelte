<script>
  import osListImport from "./data";
  let selectedTheme = "w11dark";

  let oslist = osListImport;
  oslist.forEach((os) => {
    os.show = true;
  });

  const handleInput = (e) => {
    console.log(e.target.value);
    if (!e.target.value) {
      osListImport.forEach((os, i) => {
        oslist[i].show = true;
      });
    }
    osListImport.forEach((os, i) => {
      if (os.name.toLowerCase().includes(e.target.value.toLowerCase())) {
        oslist[i].show = true;
      } else {
        oslist[i].show = false;
      }
    });
  };
</script>
  <input
    placeholder="Search OS"
    on:input={handleInput}
    type="text"
    id="searchbox"
    name="searchbox"
    list="osdatlist"
  />
  <datalist id="osdatlist">
    {#each oslist as os}
      <option>{os.name}</option>
    {/each}
  </datalist>
  <div class="card {selectedTheme}">
    <table border="1" frame="void" rules="rows">
      <tr>
        <th />
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
        <tr style:display={os.show ? "" : "none"}>
          <!-- svelte-ignore a11y-missing-attribute -->
          <td><img src={os.logo} length="20" width="20" /></td>
          <td>{os.name}</td>
          <td>{os.type}</td>
          <td>{os.build}</td>
          <td>{os.rel}</td>
          <td>{os.codename}</td>
          <td>{os.eol}</td>
          <td>{os.platform}</td>
          <td><a href={os.download}>Download</a> </td></tr
        >
      {/each}
    </table>
  </div>
<style>
  body {
    background-color: #0D1117;
  }
  table {
    table-layout: fixed;
    border-collapse: collapse;
    border-spacing: 0;
    width: fit-content;
  }
  td,
  th {
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
    height: fit-content;
    width: fit-content;
    background-color: white;
    border-radius: 5pt;
    color: black;
    padding: 1pt;
  }
</style>
