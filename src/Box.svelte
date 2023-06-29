<script>
  let state = '';
  export let boxState;
  export let handleClick;
  export let rowIndex;
  export let boxIndex;
</script>

<main>
  <button
    on:click={() => {
      handleClick(rowIndex, boxIndex);
    }}>{boxState}</button
  >
</main>

<style>
  main {
    width: 3rem;
    height: 3rem;
    background-color: green;
  }
</style>
