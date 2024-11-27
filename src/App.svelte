<script>
  import Button from './shared/Button.svelte'
  let value = 0
  let flasheffect
  let presionado = null

  function handleClick(param, buttonId) {
    presionado = buttonId
    value = value + param

    setTimeout(() => {
      presionado = null
      flasheffect = true
    }, 10)
  }
</script>

<main>
  <h1>Simple counter</h1>
  <Button on:click={() => handleClick(1, 'up')} flasheffect={presionado == 'up'}
    >Up</Button
  >

  <div class="number" class:positive={value > 0} class:negative={value < 0}>
    {value}
  </div>

  <Button
    on:click={() => handleClick(-1, 'down')}
    flasheffect={presionado == 'down'}>Down</Button
  >
</main>

<style>
  main {
    text-align: center;
    max-width: 960px;
    margin: 0 auto;
    background-color: white;
    padding: 10px 0;
    height: 100%;
  }

  h1 {
    height: 100px;
  }

  .number {
    display: flex;
    font: 48px sans-serif;
    height: 150px;
    align-items: center;
    justify-content: center;
  }

  .positive {
    color: green;
  }

  .negative {
    color: red;
  }

  @media (max-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
