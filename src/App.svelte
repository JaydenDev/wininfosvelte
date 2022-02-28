<script>
  import osListImport from "./data";
  let selectedTheme = "w11dark";

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
  
  import { onMount } from "svelte";

  // Show mobile icon and display menu
  let showMobileMenu = false;

  // List of navigation items
  const navItems = [
    { label: "WinInfo", href: "/" },
    //{ label: "Item 1", href: "#" },
    //{ label: "Item 2", href: "#" },
    //{ label: "Item 3", href: "#" },
    //{ label: "Item 4", href: "#" },
    //{ label: "Item 5", href: "#" },
    //{ label: "Item 6", href: "#" },
    //{ label: "Item 7", href: "#" }
  ];

  // Mobile menu click event handler
  const handleMobileIconClick = () => (showMobileMenu = !showMobileMenu);

  // Media match query handler
  const mediaQueryHandler = e => {
    // Reset mobile state
    if (!e.matches) {
      showMobileMenu = false;
    }
  };

  // Attach media query listener on mount hook
  onMount(() => {
    const mediaListener = window.matchMedia("(max-width: 767px)");

    mediaListener.addListener(mediaQueryHandler);
  });
</script>


<nav>
  <div class="inner">
    <div on:click={handleMobileIconClick} class={`mobile-icon${showMobileMenu ? ' active' : ''}`}>
      <div class="middle-line"></div>
    </div>
    <ul class={`navbar-list${showMobileMenu ? ' mobile' : ''}`}>
      {#each navItems as item}
        <li>
          <a href={item.href}>{item.label}</a>
        </li>
      {/each}
    </ul>
  </div>
</nav>
<br>
<div class="card" style="text-align: center">
	<h1> Warning to MacOS Catalina Users </h1>
	<p> MacOS Catalina hits EOL in 9 months </p>
	</div>
<br>
<div class="card" style="text-align: center">
	<h1> Warning to Windows 10 Users </h1>
	<p> Windows 10 hits EOL in 3 years, Computer "can't" run Windows 11? There's a solution! <a href="https://github.com/AveYo/MediaCreationTool.bat">here!</a></p>
</div>
  <h1>OSInfo</h1>
  <p>The place to go for everything OS related</p>
  <br />
  <input
    placeholder="Search OS"
    on:input={handleInput}
    style="color: black;
           width: 100%;"
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
    </table>
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
  td,
  th {
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
  .warning {
    background-color: crimson;
    width: fit-content;
    color: white;
    padding: 5px;
    border-radius: 5px;
  }
  
nav {
  background-color: transparent;
  font-family: "Helvetica Neue", "Helvetica", "Arial", sans-serif;
  height: 45px;
}

.inner {
  max-width: 980px;
  padding-left: 20px;
  padding-right: 20px;
  margin: auto;
  box-sizing: border-box;
  display: flex;
  align-items: center;
  height: 100%;
}

.mobile-icon {
  width: 25px;
  height: 14px;
  position: relative;
  cursor: pointer;
}

.mobile-icon:after,
.mobile-icon:before,
.middle-line {
  content: "";
  position: absolute;
  width: 100%;
  height: 2px;
  background-color: #fff;
  transition: all 0.4s;
  transform-origin: center;
}

.mobile-icon:before,
.middle-line {
  top: 0;
}

.mobile-icon:after,
.middle-line {
  bottom: 0;
}

.mobile-icon:before {
  width: 66%;
}

.mobile-icon:after {
  width: 33%;
}

.middle-line {
  margin: auto;
}

.mobile-icon:hover:before,
.mobile-icon:hover:after,
.mobile-icon.active:before,
.mobile-icon.active:after,
.mobile-icon.active .middle-line {
  width: 100%;
}

.mobile-icon.active:before,
.mobile-icon.active:after {
  top: 50%;
  transform: rotate(-45deg);
}

.mobile-icon.active .middle-line {
  transform: rotate(45deg);
}

.navbar-list {
  display: none;
  width: 100%;
  justify-content: space-between;
  margin: 0;
  padding: 0 40px;
}

.navbar-list.mobile {
  background-color: rgba(0, 0, 0, 0.8);
  position: fixed;
  display: block;
  height: calc(100% - 45px);
  bottom: 0;
  left: 0;
}

.navbar-list li {
  list-style-type: none;
  position: relative;
}

.navbar-list li:before {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 1px;
  background-color: #424245;
}

.navbar-list a {
  color: #fff;
  text-decoration: none;
  display: flex;
  height: 45px;
  align-items: center;
  padding: 0 10px;
  font-size: 13px;
}

@media only screen and (min-width: 767px) {
  .mobile-icon {
    display: none;
  }

  .navbar-list {
    display: flex;
    padding: 0;
  }

  .navbar-list a {
    display: inline-flex;
  }
}

</style>
