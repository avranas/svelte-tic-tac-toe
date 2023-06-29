<script>
  import Row from './Row.svelte';
  const winningConditions = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6],
  ];
  let state = [
    ['-', '-', '-'],
    ['-', '-', '-'],
    ['-', '-', '-'],
  ];
  let turnCount = 0;
  let turn = 'X';
  let gameOver = false;
  let message = '';

  export function handleClick(x, y) {
    if (state[x][y] !== '-') return;
    if (gameOver) return;
    turnCount++;
    if (turnCount === 9) {
      gameOver = true;
      message = "It's a draw!"
    }
    state[x][y] = turn;
    const test = [];
    for (let x = 0; x < state.length; x++) {
      for (let y = 0; y < state[0].length; y++) {
        test.push(state[x][y]);
      }
    }
    winningConditions.forEach((c) => {
      if (
        test[c[0]] === test[c[1]] &&
        test[c[1]] === test[c[2]] &&
        test[c[0]] === test[c[2]] &&
        test[c[0]] !== '-'
      ) {
        gameOver = true;
        message = `${turn} is the winner!`
      }
    });
    turn = turn === 'X' ? 'O' : 'X';
  }
</script>

<main>
  {#each state as row, i}
    <Row rowState={row} {handleClick} rowIndex={i} />
  {/each}
  {#if !gameOver}
    <p>Turn: {turn}</p>
  {:else}
    <p>{message}</p>
  {/if}
</main>

<style>
  main {
    width: 9rem;
    height: 9rem;
    background-color: blue;
  }
</style>
