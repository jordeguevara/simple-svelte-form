<script>
  import CheckMark from "./Check.svelte";
  let name = "";
  let expanded = false;
  const changeExpanded = () => {
    expanded = !expanded;
  };
  let completed = false;

  const toggle = () => (completed = !completed);
</script>

<main class="main">
{#if completed}
  <p>Some Other page</p>
{:else}
  <div class={expanded ? 'form--collapse' : 'form'}>
    {#if !expanded}
      <h1 style="padding:1rem">Tell us about yourself</h1>
      <div class="child">
        <input bind:value={name} placeholder="Name" />
        <input placeholder="Title" />
      </div>
    {/if}
    <div class="child">
      <div class={expanded ? 'container--expanded' : 'container'}>
        {#if expanded}
          <h3 class="title input--expanded child">
            Thanks for the input, {name}!
          </h3>
          <p class="input--expanded">
            Want to leave any closing remarks?(Optional)
          </p>
          <textarea
            style="margin: .5rem 2rem 3rem 2rem;"
            placeholder="I wanted to let you guys know that..."
            class="input--expanded child" />
        {/if}
        <button
          class={expanded ? 'submitted--expanded' : 'submitted'}
          class:disabled={!name ? true : false}
          disabled={name ? false : true}
          on:click={expanded ? toggle : changeExpanded}>
          {#if expanded}
            <CheckMark {completed} {toggle} />
          {:else}Submit{/if}
        </button>
      </div>
    </div>
  </div>
{/if}

</main>

<style>
  .submitted {
    height: 4rem;
    width: 20rem;
    border-radius: 2.5rem;
    border: none;
    background: linear-gradient(90deg, #4df5bd 50%, #21f3ad 100%);
    color: #fff;
    font-size: 1.25rem;
    box-shadow: 4px 3px rgb(241, 241, 241);
    transition: height 0.35s;
    font-weight: 700;
    letter-spacing: 0.1rem;
    box-shadow: 1px 1px 10px #b7fbe4;
  }

  .disabled {
    height: 4rem;
    width: 20rem;
    border-radius: 2.5rem;
    border: none;
    background: #ccc;
    color: #fff;
    font-size: 1.25rem;
    box-shadow: 4px 3px rgb(241, 241, 241);
    transition: height 0.35s;
  }

  .submitted--expanded {
    transition: height 1s, font-size 0.3s border-radius 0.3s;
    height: 3rem;
    min-width: 20rem;
    border-radius: 0;
    border: none;
    background-color: rgb(33, 243, 173);
    color: #fff;
    border-bottom-right-radius: 2rem;
    border-bottom-left-radius: 2rem;
    font-size: 1.25rem;
    transition-delay: 0.1s;
    box-shadow: 4px 3px rgb(223, 221, 221);
  }

  .container {
    height: 4rem;
    width: 20rem;
    display: flex;
    background-color: rgb(33, 243, 173);
    border-radius: 2.5rem;
  }

  .container--expanded {
    background-color: #fff;
    height: 20rem;
    min-width: 20rem;
    transition: height 0.25s, border-radius 0.1s, background-color 0.75s;
    display: flex;
    flex-direction: column;
    border-radius: 2rem;
    box-shadow: 1px 1px 10px #d2d2d2;
    transition-timing-function: ease;
    transition-delay: 0.05s;
  }

  .title {
    padding: 1rem;
  }

  .child {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .input--expanded {
    animation: textFade 0.6s;
    animation-timing-function: ease-out;
    margin: 0.25rem 2rem;
  }

  @keyframes textFade {
    0% {
      opacity: 0;
    }
    50% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  .form {
    background: #fff;
    height: 25rem;
    width: 40rem;
    border-radius: 1rem;
    display: flex;
    flex-direction: column;
    padding: 1.5rem;
    box-sizing: border-box;
    box-shadow: 1px 1px 10px #d2d2d2;
  }

  .form--collapse {
    /* width: 20rem;
                                height: 10rem;
                                background-color:#fff;
                                transition:  height .5s; */
  }

  input {
    width: 45%;
    height: 4rem;
    border-radius: 10px;
    border: none;
    margin: 0.25rem 0.5rem;
    font-size: 1rem;
    background-color: #f5f6f8;
    padding-left: 1rem;
  }

  textarea {
    font-size: 1rem;
    margin: 1rem;
    border: 1px solid rgb(228, 228, 228);
    padding: 1rem;
  }

  p {
    margin: 0 1rem;
    color: rgb(180, 180, 180);
    font-size: 0.85rem;
  }

  .main {
    position: relative;
    width: 100vw;
    height: 100vh;
    background-color: #ededed;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #333;
    margin: 0;
    padding: 8px;
    box-sizing: border-box;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
      Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", sans-serif;
    font-size: 16px;
  }

  @media screen and (max-width: 320px) {
    .main {
      background: green;
      font-size: 8px;
    }
  }
</style>