<script lang="ts">
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'
  import "./app.css"

  /**logic for the audio element**/
  let audio: HTMLAudioElement | null = null;
  let timeoutId: number | null = null; // play only 10 seconds
  let playButton = document.getElementById("play");
  let isPlaying = false;
  function playAudio() {
    if(audio) {
      audio.play();
      isPlaying = true;
    }
  }

</script>

<div class="bg-grey-300 min-h-screen flex text-center items-center justify-center">
  <div class="bg-purple-200 p-10 rounded w-full max-w-lg max-h-screen shadow-md">
    <h1 class="text-3xl ">music trivia!</h1>
    <div class="mb-6 mr-5">
      <button id=play class="w-1/4 mt-10 mb-5 bg-green-800 hover:bg-red-300 py-2 px-4 rounded duration-500 transform hover:scale-110 transition ease-linear" on:click={playAudio} disabled={isPlaying}>{isPlaying ? 'Playing...' : 'Play Audio'}</button>
      <audio bind:this={audio} src="/hysteria.mp3"></audio>
      {#if isPlaying} 
        <canvas class="w-full h-24 mb-6 bg-slate-200 rounded "></canvas>
      {/if}
      <div class="space-y-4">
        <div>
          <label for="song-guess" class="block text-sm text-left ml-3 font-medium text-gray-800">song:</label>
          <input type="text"
          id=song-guess
          placeholder="enter the song name"
          class="border px-4 py-2 rounded w-3/4"
          >
          <button class="border px-4 py-2 w-1/ bg-red-50 duration-300 transform hover:scale-105 transition ease-linear">enter</button>
          <label for="artist-guess" class="block text-sm text-left ml-3 font-medium text-gray-800">by:</label>
          <input type="text"
          id=artist-guess
          placeholder="enter the artist name"
          class="border px-4 py-2 rounded w-3/4"
          >
          <button class="border px-4 py-2 w-1/ bg-red-50 duration-300 transform hover:scale-105 transition ease-linear">enter</button>
        </div>
      </div>
    </div>
  </div>
</div>




