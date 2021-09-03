<script lang="ts">
  import { onMount } from 'svelte';

  let data: string;

  onMount(async function () {
    const response = await fetch('http://localhost:8080/hello');
    console.log(response);
    data = (await response.json()).data;
  });
</script>

<main>
  Hello
  {data}
</main>

<style global lang="postcss">
  @tailwind base;
  @tailwind components;
  @tailwind utilities;

  .loader {
    border: 2px solid #f3f3f3;
    border-top: 2px solid #ff3e00;
    border-radius: 50%;
    width: 20px;
    height: 20px;
    animation: spin 2s linear infinite;
    margin: auto;
  }

  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>
