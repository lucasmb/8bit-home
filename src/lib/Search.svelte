<script>
  let searchstring = '';
  let engine = 'ecosia';
  const searchengines = [
    { title: 'Ecosia', key: 'ecosia', url: 'https://ecosia.org/search?q=' },
    { title: 'Google', key: 'google', url: 'https://google.com/search?q=' },
    { title: 'DuckDuckGo', key: 'ddgo', url: 'https://duckduckgo.com/?q=' }
  ];
  function search() {
    const eng = searchengines.find((val) => val.key === engine);
    if (searchstring) window.location.assign(eng.url + searchstring);
  }
</script>

<div class="flex-container">
  <form on:submit|preventDefault={search}>
    <div class="search-input">
      <input
        bind:value={searchstring}
        type="text"
        placeholder="search"
        id="name_field"
        class="nes-input"
      />
      <button type="submit" class=" btn nes-btn is-primary">Search</button>
    </div>
    <div>
      {#each searchengines as item, i}
        <label>
          <input type="radio" class="nes-radio" bind:group={engine} value={item.key} />
          <span>{item.title}</span>
        </label>
      {/each}
    </div>
  </form>
</div>
<div>
  <!-- or with adnditional index value -->
</div>

<style>
  .search-input {
    display: flex;
  }
  .btn {
    box-sizing: border-box;
    display: inline-block;
  }
</style>
