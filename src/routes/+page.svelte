<script>
  import Card from '$lib/Card.svelte';

  let strategies = [
    'Use an old idea',
    'State the problem in words',
    'Try faking it',
    'Honor thy error',
    'What would your friend do?',
    'Take a break',
    'Discard assumptions',
    'Use fewer elements',
    'Give the game away',
    'Reverse roles',
    'Emphasize the flaws',
    'Repetition is a form of change',
    'Remove the middle',
    'Is it finished?',
    'Do the words need changing?',
    'Make it more primitive',
    'Change nothing and continue',
    'Use an unacceptable color',
    'Allow an accident',
    'Imagine the piece as a tiny model',
    'Do something boring',
    'Disconnect from desire',
    'Work at a different speed',
    'Ask your body',
    'Make a sudden, destructive action',
    'Use an element of chance',
    'Go outside. Shut the door.',
    'Only one element at a time',
    "Don't be afraid of clichés",
    'Slow down. Even more.',
    'Use silence',
    'Would anyone notice?',
    'Do the last thing first',
    "Imagine it's a cover version",
    'Intuition beats intellect here',
    "What if it's already done?",
    'Overdo it. Then scale back.',
    "Don't stress — it's weird",
  ];

  let used_strategies = [''];

  let flipped = false;
  let flipping = false;
  let currentFront = 'Oblique Strategies';
  let currentBack = '';

  function randomStrategy() {
    if (used_strategies.length - 1 === strategies.length) {
      used_strategies = [''];
    }
    let new_idx = Math.floor(Math.random() * strategies.length);
    while (used_strategies.includes(strategies[new_idx])) {
      new_idx = Math.floor(Math.random() * strategies.length);
    }
    used_strategies.push(strategies[new_idx]);
    console.log(used_strategies);
    return strategies[new_idx];
  }

  async function handleCardClick() {
    if (flipping) return;
    flipping = true;

    flipped = !flipped;

    setTimeout(() => {
      currentBack = flipped ? randomStrategy() : '';
      flipping = false;
    }, 150);
  }
</script>

<svelte:head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
</svelte:head>

<div class="flex min-h-screen items-center justify-center bg-[#faf8f2]">
  <button type="button" on:click={handleCardClick} class="card-button">
    <Card front={currentFront} back={currentBack} {flipped} />
  </button>
</div>

<style>
  .card-button {
    all: unset;
    display: inline-block;
    cursor: pointer;
  }
</style>
