<script>
  import Box from './Box.svelte';
  export let rowState;
  export let handleClick;
  export let rowIndex;
  let state = '';
</script>

<main>
  {#each rowState as boxState, i}
    <Box {boxState} {handleClick} boxIndex={i} {rowIndex}/>
  {/each}
</main>

<style>
  main {
    display: flex;
    width: 9rem;
    height: 3rem;
    background-color: red;
  }
</style>
