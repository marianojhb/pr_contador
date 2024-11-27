<script>
  export let flasheffect
</script>

<button on:click class:flasheffect>
  <slot></slot>
</button>

<style>
  button {
    position: relative;
    box-sizing: border-box;
    padding: 0px;
    margin: 0px;
    width: 150px;
    height: 150px;
    background-color: #ddd;
    cursor: pointer;
    z-index: 5;
  }

  button:hover {
    color: white;
    border: solid 1px black;
  }

  button:not(:hover) {
    border: solid 1px #cbcdcb;
  }

  .flasheffect {
    animation-name: flasheffect;
    animation-duration: 0.1s;
  }

  @keyframes flasheffect {
    0% {
      opacity: 0;
    }
    25% {
      opacity: 0.25;
    }
    75% {
      opacity: 0.7;
    }
    100% {
      opacity: 0.99;
    }
  }
</style>
