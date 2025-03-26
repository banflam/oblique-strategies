<script>
  export let front = '';
  export let back = '';
  export let flipped = false;
</script>

<div class="perspective relative aspect-[3/2] h-auto w-[40vw] cursor-pointer">
  <div
    class={`transform-style-preserve-3d relative h-full w-full transition-transform duration-300 ${flipped ? 'rotate-y-180' : ''}`}
  >
    <div
      class="backface-hidden absolute flex h-full w-full items-center justify-center rounded-2xl bg-black p-4 text-center text-2xl text-white shadow-md"
    >
      {front}
    </div>

    <div
      class="backface-hidden rotate-y-180 absolute flex h-full w-full items-center justify-center rounded-2xl bg-gray-100 p-4 text-center text-2xl shadow-md"
    >
      {back}
    </div>
  </div>
</div>

<style>
  .perspective {
    perspective: 1000px;
  }
  .transform-style-preserve-3d {
    transform-style: preserve-3d;
  }
  .backface-hidden {
    backface-visibility: hidden;
  }
  .rotate-y-180 {
    transform: rotateY(180deg);
  }
</style>
