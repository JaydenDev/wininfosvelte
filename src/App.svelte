<script>
  import osListImport from "../OSInfo-Data/data";
  import "./out.css"

  let oslist = osListImport;
  oslist.forEach((os) => {
    os.show = true;
  });

  const handleInput = (e) => {
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
  const handleAlert = () => {
    let alert = document.querySelector(".alert");
    alert.classList.add('hidden');
    if (oslist.every((os) => os.show === false)) {
      alert.style.display = "block";
      let table = document.querySelector("#dat");
      table.classList.add('hidden')
    } else {
      alert.style.display = "none";
      let table = document.querySelector("#dat");
      table.classList.remove('hidden')
    }
    let input = document.querySelector("#searchbox");
    if (!input.value) {
      let table = document.querySelector("#dat");
      table.classList.remove('hidden')
    }
  };

  function catalina() {
    if (navigator.userAgent.includes("Macintosh")) {
      document.getElementById("catalinaDet").classList.remove("hidden");
      console.log("DEBUG: Mac OS X Catalina detected.");
      return true;
    } else {
      console.log("DEBUG: Alternate Detected, Operation Ignored.")
      return false;
    }
  }
  catalina()
</script>
<body class="text-white">
<div class="">
  <div class="bg-emerald-500 flex space-x-2 m-2 rounded-lg p-8">
    <h1 class="text-4xl">OSInfo</h1>
    <p class="text-4xl">The place to go for everything OS related</p>
  </div>
  <br />
  <div id="catalinaDet" class="hidden m-2 bg-red-500 p-3 text-white rounded-lg">
    <h1> Warning to MacOS Catalina Users </h1>
    <p> MacOS Catalina hits EOL in 5 and a half months </p>
 </div>
  <div id="win10det" class="hidden bg-red-500 p-3 text-white rounded-lg m-2 p">
    <h1> Warning to Windows 10 Users </h1>
    <p> Windows 10 hits EOL in 1 year, Computer "can't" run Windows 11? There's a solution! <a href="https://github.com/AveYo/MediaCreationTool.bat">here!</a></p>
 </div>
</div>
  <input
    placeholder="Search OS"
    on:input={handleInput}
    on:input={handleAlert}
    class="p-3 rounded-lg text-black m-2 w-[95vw]"
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
  <div class="text-white hidden bg-red-500 p-3 rounded-lg alert"><p>No results for query</p></div>
  <div id="dat" class="bg-gray-800 text-xl rounded-lg m-8 p-8">
    <table id="data-table" border="1" frame="void" rules="rows">
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
          <td><img src={os.logo} length="40" width="40" /></td>
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
      <style>
        body {
          background-size: cover;
          background-repeat: no-repeat;
          background-position: center;
          background-attachment: fixed;
          background-image: url('https://jdev.eu.org/img/bg.svg')
        }
      </style>
    </table>
    </div>
</body>