<section class={$$props.class} style={$$props.style || null}>
  <slot />
</section>

<style>
  section {
    width: 100%;
    /* display: flex;
    flex-direction: column; */
    background-color: var(--primary);
    padding: 20px;
    display: flex;
    flex-direction: column;
  }

  /* @media only screen and (min-width: 800px) {
    section {
      flex-direction: row;
    }
  } */

  @media only screen and (min-width: 800px) {
    section {
      padding: 40px;
    }
  }

  @media only screen and (min-width: 1400px) {
    section {
      padding: 80px 200px;
    }
  }
</style>
