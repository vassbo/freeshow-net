<script lang="ts">
  import Icon from "../../../components/Icon.svelte"

  // y, n, ?, ~
  // freeshow, propresenter, easyworship, videopsalm, openlp, proclaim, (mediashout), powerpoint
  // fs, pp, ew, vp, ol, pc, ms
  const features: any = [
    {
      name: "Price",
      programs: { fs: "Free", pp: "$399", ew: "$180/yr", vp: "Free", ol: "Free", pc: "$225/yr" },
      note: { pp: "Starting at $399", ew: "Starting at $180 yearly", pc: "Starting at $255 yearly" },
    },
    { name: "Platforms", programs: { fs: "{win}{mac}{linux}", pp: "{win}{mac}", ew: "{win}", vp: "{win}", ol: "{win}{mac}{linux}", pc: "{win}{mac}" } },
    {
      name: "Multiple languages",
      programs: { fs: "{y}", pp: "{y}", ew: "{n}", vp: "{y}", ol: "{y}", pc: "{y}" },
      note: {
        fs: "English, Norwegian, Spanish, Slovak & more comming",
        pp: "10 languages",
        ew: "Only english",
        vp: "Around 50 languages",
        ol: "At least 26 languages",
        pc: "English & Spanish",
      },
    },
    {
      name: "Customer support",
      programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{y}", pc: "{y}" },
      note: { fs: "Via email or GitHub", ew: "With subscription", vp: "Via email", ol: "Forums" },
    },
    {
      name: "Projects",
      info: "Create and manage multiple projects",
      programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{y}", pc: "{y}" },
      note: { ew: "Stored as files on the computer", vp: "Stored as files on the computer" },
    },
    { name: "Slides", info: "Create and edit slides", programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{y}", pc: "{y}" } },
    {
      name: "Groups",
      info: "Create groups and reuse slides",
      programs: { fs: "{y}", pp: "{y}", ew: "{n}", vp: "{n}", ol: "{y}", pc: "{y}" },
      note: { ol: "Text based", pc: "Text based" },
    },
    { name: "Preview", info: "Output preivew and slide preview", programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{y}", pc: "{y}" }, note: { vp: "Only text" } },
    { name: "Quick lyrics", programs: { fs: "{y}", pp: "{y}", ew: "{n}", vp: "{n}", ol: "{n}", pc: "{y}" } },
    { name: "Text edit", info: "Edit a whole show like a text file", programs: { fs: "{n}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{y}", pc: "{y}" }, note: { fs: "Planned" } },
    { name: "RTE", info: "Rich text editor", programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{n}", pc: "{y}" } },
    { name: "Chords", info: "Add chords in text", programs: { fs: "{n}", pp: "{n}", ew: "{n}", vp: "{y}", ol: "{y}", pc: "{n}" }, note: { fs: "Planned" } },
    { name: "Auto labels", programs: { fs: "{y}", pp: "{y}", ew: "{n}", vp: "{y}", ol: "{y}", pc: "{n}" } },
    { name: "Slide actions", info: "Add actions to happen when slide is enabled", programs: { fs: "{y}", pp: "{y}", ew: "{n}", vp: "{n}", ol: "{n}", pc: "{y}" } },
    { name: "Transitions", programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{n}", pc: "{y}" }, note: { ew: "Can't be changed easily" } },
    { name: "Timers", programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{y}", pc: "{y}" }, note: { fs: "WIP" } },
    {
      name: "Media",
      info: "Preview media and set as background",
      programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{y}", pc: "{y}" },
      note: { ew: "Hard to use", vp: "Hard to use", ol: "Hard to use", pc: "Only one background per slideshow" },
    },
    { name: "Overlays", programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{n}", pc: "{y}" } },
    { name: "Music", info: "Play audio", programs: { fs: "{n}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{n}", pc: "{y}" }, note: { fs: "Planned" } },
    { name: "Bibles", programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{y}", pc: "{y}" } },
    { name: "Calendar", info: "Create events and schedule shows", programs: { fs: "{y}", pp: "{n}", ew: "{n}", vp: "{n}", ol: "{n}", pc: "{y}" } },
    { name: "Lock output", info: "Prevent changes to the output", programs: { fs: "{y}", pp: "{n}", ew: "{n}", vp: "{n}", ol: "{n}", pc: "{n}" } },
    { name: "Remote controller", programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{n}", ol: "{y}", pc: "{y}" }, note: { pp: "Costs $4.99" } },
    { name: "Stage display", programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{y}", pc: "{y}" } },
    {
      name: "Mirror screen",
      info: "Show a live mirror of a screen or window on the presenters computer",
      programs: { fs: "{y}", pp: "{n}", ew: "{n}", vp: "{n}", ol: "{n}", pc: "{n}" },
    },
    { name: "Cameras", programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{n}", pc: "{y}" } },
    { name: "YouTube", info: "Play YouTube videos inside the program", programs: { fs: "{y}", pp: "{n}", ew: "{n}", vp: "{n}", ol: "{n}", pc: "{n}" } },
    { name: "NDI support", info: "Multiple outputs", programs: { fs: "{n}", pp: "{y}", ew: "{y}", vp: "{n}", ol: "{n}", pc: "{n}" }, note: { fs: "Planned" } },
    { name: "MIDI support", info: "MIDI controllers", programs: { fs: "{n}", pp: "{y}", ew: "{y}", vp: "{n}", ol: "{n}", pc: "{y}" }, note: { fs: "Planned" } },
    { name: "CCLI", info: "Church Copyright Licensing International", programs: { fs: "{n}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{y}", pc: "{y}" }, note: { fs: "Planned" } },
    { name: "Import PowerPoint", programs: { fs: "{y}", pp: "{y}", ew: "{y}", vp: "{y}", ol: "{y}", pc: "{y}" } },
    { name: "Export as PDF", programs: { fs: "{y}", pp: "{y}", ew: "{n}", vp: "{n}", ol: "{n}", pc: "{n}" } },
    { name: "Continious mode", info: "Show all project elements on one continious page", programs: { fs: "{n}", pp: "{y}", ew: "{n}", vp: "{n}", ol: "{n}", pc: "{y}" } },
    { name: "Draw", info: "Draw/point over output", programs: { fs: "{y}", pp: "{y}", ew: "{n}", vp: "{n}", ol: "{n}", pc: "{n}" } },
    { name: "Themes", info: "Customize the look of the application", programs: { fs: "{y}", pp: "{n}", ew: "{n}", vp: "{y}", ol: "{n}", pc: "{n}" }, note: { vp: "Skins" } },
  ]
</script>

<section>The number one difference is definetly the price!</section>

<section style="width: 100%;overflow: auto;">
  <table>
    <tr>
      <th>Feature</th>
      <th><a href="https://freeshow.app/" target="_blank">FreeShow</a></th>
      <th><a href="https://renewedvision.com/propresenter/" target="_blank">ProPresenter</a></th>
      <th><a href="https://www.easyworship.com/" target="_blank">EasyWorship</a></th>
      <th><a href="https://myvideopsalm.weebly.com/" target="_blank">VideoPsalm</a></th>
      <th><a href="https://openlp.org/" target="_blank">OpenLP</a></th>
      <th><a href="https://faithlife.com/products/proclaim" target="_blank">ProClaim</a></th>
    </tr>
    {#each features as feature}
      <tr>
        <td class:info={feature.info} style="padding: 2px 6px;display: flex;gap: 10px;align-items: center;">
          {feature.name}
          {#if feature.info}
            <div class="info">
              <Icon id="info" size={0.7} color="rgb(255 255 255 / 0.6)" />
              <div class="hidden">
                {feature.info}
              </div>
            </div>
          {/if}
        </td>
        {#each Object.keys(feature.programs) as id}
          <td class:note={feature.note?.[id]}>
            <div class="content">
              {#if feature.programs[id].includes("{win}")}
                <Icon id="windows" color="#0078D7" />
              {/if}
              {#if feature.programs[id].includes("{mac}")}
                <Icon id="mac" color="#999999" />
              {/if}
              {#if feature.programs[id].includes("{linux}")}
                <Icon id="linux" color="#dd4814" />
              {/if}
              {#if feature.programs[id].includes("{y}")}
                <Icon id="yes" color="#19e119" />
              {/if}
              {#if feature.programs[id].includes("{n}")}
                <Icon id="no" color="#ff4d4d" />
              {/if}
              {feature.programs[id].replace(/(\{.*?\})/g, "")}
            </div>
            {#if feature.note?.[id]}
              <div class="hidden">
                {feature.note?.[id]}
              </div>
            {/if}
          </td>
        {/each}
      </tr>
    {/each}
  </table>
</section>

<style>
  table {
    /* border-spacing: 0; */
    width: 100%;
  }

  th {
    padding: 2px 6px;
  }

  th,
  td {
    text-align: left;
    transition: 0.1s filter;
  }

  td .content {
    position: relative;
    padding: 2px 6px;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 5px;
    cursor: default;
  }

  th a {
    color: var(--text);
  }

  table tr:nth-child(odd) {
    background-color: rgb(255 255 255 / 0.1);
  }

  /* info */

  td.info:hover > div .hidden {
    display: block;
  }

  /* note */

  td.note .content::after {
    content: "*";
    color: rgb(255 255 255 / 0.6);
    /* color: #ff9999; */
    position: absolute;
    right: 10px;
  }
  td.note .content:hover {
    filter: brightness(0.8);
  }

  .hidden {
    position: absolute;
    padding: 8px;
    background-color: var(--primary);
    box-shadow: 1px 1px 5px rgb(0 0 0 / 0.2);
    font-style: italic;
    white-space: nowrap;
    filter: brightness(0.9);
    display: none;
    z-index: 10;
    pointer-events: none;
    /* opacity: 0; */
    /* transition: 0.2s opacity; */
  }
  td:hover > .hidden {
    display: block;
    /* opacity: 1; */
  }
</style>
