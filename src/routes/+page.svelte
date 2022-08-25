<script>
  import { onMount } from 'svelte';
  import Search from '$lib/Search.svelte';
  // Inject the time in the UI
  const renderTime = function () {
    let time = new Date();
    return time.toLocaleString('en-US', {
      year: 'numeric',
      month: 'long',
      day: 'numeric',
      hour: 'numeric',
      minute: 'numeric',
      second: 'numeric',
      hour12: true
    });
  };

  let clock = renderTime();

  onMount(() => {
    const interval = setInterval(() => {
      clock = renderTime();
    }, 1000);
  });
</script>

<nav style="padding: 20px; border-bottom: 3px solid #ccc; margin-bottom: 60px;">
  <div class="container">
    <h2 style="margin-bottom: 0;">
      <i class="snes-jp-logo" />
      8Bit-Home
    </h2>
  </div>
</nav>

<main class="flex-container2">
  <div id="clock" class="flex-item1">{clock}</div>
  <Search />
</main>
