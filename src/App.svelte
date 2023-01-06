<script lang="ts">
  import VideoCall from './lib/VideoCall/VideoCall.svelte';
  let myId, theirId;
  let call = false;
  let defaults = {video: true, audio: true}
</script>

<main>
  {#if !call}
  <input placeholder="my name" bind:value={myId} type="text"/>
  <input placeholder="connect to name" bind:value={theirId} type="text" />
  <button on:click={() => call = true}>call</button>
  {/if}
</main>

{#if call}
  <VideoCall
    userData={{id: myId}}
    targetData={{id: theirId}}
    onHangup={() => call = false}
    defaults={defaults}
  />
{/if}