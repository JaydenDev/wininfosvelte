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
  {#each windowslist as windows}
      <pre>
        <p> {windows.name}    {windows.build}    {windows.rel}    {windows.codename} </p>
        <hr style="width: 75%">
      </pre>
  {/each}
  </div>
</div>

<style>
  /* button {
    border-radius: 5pt;
  } */
  
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
    height: 100%;
    width: 75%;
    background-color: white;
    border-radius: 5pt;
    color: black;
  }

</style>
