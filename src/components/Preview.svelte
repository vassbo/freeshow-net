<script lang="ts">
  import Fullscreen from "./Fullscreen.svelte"
  import Section from "./Section.svelte"

  export let preview: null | string = null
</script>

{#if preview}
  <Fullscreen src="./preview/{preview}.jpg" alt="Preview of program" bind:preview />
{/if}

<Section>
  <h2>Preview</h2>
  <div class="previews">
    <div>
      <span>
        <h3>Show</h3>
        <p>
          Create a show for a song, or a slideshow, or some information. Add slides and arrange them by groups. Create different layouts for the same slides. Preview slides and
          have full control over the output.
        </p>
      </span>
      <img on:click={() => (preview = "show")} src="./preview/show.jpg" alt="Show" />
    </div>
    <hr />
    <div>
      <span>
        <h3>Lyrics</h3>
        <p>Change slide preivew to lyrics mode if it is preferred.</p>
      </span>
      <img on:click={() => (preview = "lyrics_view")} src="./preview/lyrics_view.jpg" alt="Lyrics View" />
    </div>
    <hr />
    <div>
      <span>
        <h3>Edit</h3>
        <p>A powerful editor. It is easy to make changes while presenting. Resize text, change font family or color, and much more. The posibilities are endless (almost)!</p>
      </span>
      <img on:click={() => (preview = "edit")} src="./preview/edit.jpg" alt="Edit" />
    </div>
    <hr />
    <div>
      <span>
        <h3>Stage</h3>
        <p>
          Connect using the computer IP + default port 5511 from any browser on the same network. Create and edit multiple stage views. Add current and next slide, or a countdown
          timer. Anyone on the same WiFi can connect from the browser and choose a view. You can add a password to a view.
        </p>
      </span>
      <img on:click={() => (preview = "stage")} src="./preview/stage.jpg" alt="Stage" />
    </div>
    <hr />
    <div>
      <span>
        <h3>Draw</h3>
        <p>Shine a light on your slides while presenting. Or draw a beautiful drawing, (TBA).</p>
      </span>
      <img on:click={() => (preview = "draw")} src="./preview/draw.jpg" alt="Draw" />
    </div>
    <hr />
    <div>
      <span>
        <h3>Calendar</h3>
        <p>A calendar for all your events, select dates and create a show with info about upcomming events. Or schedule shows to play, or timers to start (TBA).</p>
      </span>
      <img on:click={() => (preview = "calendar")} src="./preview/calendar.jpg" alt="Calendar" />
    </div>

    <hr />
    <div>
      <span>
        <h3>Themes</h3>
        <p>Create you own themes, tweak the colors and UI to the extreme.</p>
      </span>
      <img on:click={() => (preview = "customize")} src="./preview/customize.jpg" alt="Customize" />
    </div>
    <!-- groups -->
    <hr />
    <div>
      <span>
        <h3>Media</h3>
        <p>Show images/videos easily. Add filters and link them to your shows.</p>
      </span>
      <img on:click={() => (preview = "media")} src="./preview/media.jpg" alt="Media" />
    </div>
    <hr />
    <div>
      <span>
        <h3>Scripture</h3>
        <p>Import your own from a local file, or select from over 100 bibles from <a href="https://scripture.api.bible/" target="_blank">API.Bible</a>.</p>
      </span>
      <img on:click={() => (preview = "scripture")} src="./preview/scripture.jpg" alt="Scripture" />
    </div>
    <!-- <hr />
      <div>
        <span>
          <h3>Stage View</h3>
          <p>Setup stage views on any device.</p>
        </span>
        <img on:click={() => (preview = "stage_view")} src="./preview/stage_view.jpg" alt="Stage View" />
      </div> -->
    <hr />
    <div>
      <span>
        <h3>Remote</h3>
        <p>
          Connect using the computer IP + default port 5510 from any browser on the same network. Control your project from your phone, with an easy-to-navigate interface. You can
          even view lyrics from the active show.
        </p>
      </span>
      <span class="width">
        <img style="width: initial;" on:click={() => (preview = "remote")} src="./preview/remote.jpg" alt="Remote" />
        <img style="width: initial;" on:click={() => (preview = "lyrics")} src="./preview/lyrics.jpg" alt="Lyrics" />
      </span>
    </div>
  </div>
</Section>

<style>
  h2,
  h3 {
    color: var(--secondary);
    text-align: center;
  }

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    user-select: none;
  }

  hr {
    height: 3px;
    background-color: var(--primary-darker);
    width: 100%;
    border: none;
  }

  .previews {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }
  .previews div {
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    gap: 10px;
  }
  .previews span,
  .previews img {
    max-height: 300px;
    object-fit: contain;
  }

  .width {
    display: flex;
    justify-content: center;
    gap: 10px;
  }

  div :global(a) {
    color: var(--secondary);
    font-weight: bold;
    transition: background-color 0.3s;
  }
  div :global(a):hover {
    background-color: rgb(0 0 0 / 0.3);
  }

  @media only screen and (min-width: 800px) {
    h2 {
      text-align: initial;
    }

    .previews div {
      flex-direction: row;
    }
    .previews span,
    .previews img,
    .width {
      width: 50%;
    }
  }
</style>
