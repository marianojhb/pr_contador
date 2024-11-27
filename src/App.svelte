<script>
  import Button from './shared/Button.svelte'
  let value = 0
  let flasheffect
  let presionado = null
  let efectoCuentaGanado
  let efectoCuentaGanadoDown

  function handleClick(param, buttonId) {
    presionado = buttonId

    setTimeout(() => {
      value = value + param
      presionado = null
      flasheffect = true
      efectoCuentaGanado = true
      efectoCuentaGanadoDown = true
      // console.log(efectoCuentaGanado)
    }, 400)
  }
</script>

<main>
  <h1>Simple counter</h1>
  <Button on:click={() => handleClick(1, 'up')} flasheffect={presionado == 'up'}
    >Up</Button
  >

  <div
    class="number"
    class:positive={value > 0}
    class:negative={value < 0}
    class:efectoCuentaGanado={presionado == 'up'}
    class:efectoCuentaGanadoDown={presionado == 'down'}
  >
    {value}
  </div>

  <Button
    on:click={() => handleClick(-1, 'down')}
    flasheffect={presionado == 'down'}>Down</Button
  >

  <p>
    <em>El numero es </em>
    {value > 0 ? 'Positivo' : value < 0 ? 'Negativo' : 'Nulo'}
  </p>

  <button on:click={() => (value = 0)}>RESET </button>
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
    width: 150px;
    margin: 0px auto;
    position: relative;
    z-index: 1;
  }

  .efectoCuentaGanado {
    position: relative;
    animation-name: baja;
    animation-duration: 0.46s;
    animation-timing-function: ease-in-out;
    top: 0px;
    z-index: 2;
  }

  @keyframes baja {
    0% {
      transform: translateY(0); /* Initial position */
      color: lime;
    }
    30% {
      transform: translateY(150px); /* Move to top */
    }
    60% {
      transform: translateY(-150px); /* Move to bottom */
      clip-path: inset(100% 0 0 0);
    }
    100% {
      transform: translateY(0); /* Return to original position */
      clip-path: inset(0 0 0 0);
    }
  }
  .efectoCuentaGanadoDown {
    position: relative;
    animation-name: sube;
    animation-duration: 0.46s;
    animation-timing-function: ease-in-out;
    top: 0px;
    z-index: 2;
  }

  @keyframes sube {
    0% {
      transform: translateY(0); /* Initial position */
      color: fuchsia;
    }
    30% {
      transform: translateY(-150px); /* Move to top */
    }
    60% {
      transform: translateY(150px); /* Move to bottom */
      clip-path: inset(100% 0 0 0);
    }
    100% {
      transform: translateY(0); /* Return to original position */
      clip-path: inset(0 0 0 0);
    }
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
