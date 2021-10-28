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
  {#each windowslist as windows}
    <div class="card {selectedTheme}">
      <pre>
        <p> {windows.name}    {windows.build}    {windows.rel}    {windows.codename} </p>
      </pre>
    </div>
  {/each}
</div>

<style>
  /* button {
    border-radius: 5pt;
  } */
  
  * {
    color: white;
  }
  
  .container {
    width: 100vw;
    min-height: 100vh;
    padding: none;
    margin: none;
  }
  
  .card {
    height: 100%;
    width: 75%;
    background-color: white;
    border-radius: 5pt;
    color: black;
    padding: 5px;
  }

</style>
