<script>
  export let showModalTips = false;
  export let closeModalTips;

  // List of tips for saving food
  const tips = [
    "Plan meals ahead to avoid buying unnecessary items.",
    "Store food properly to extend its shelf life.",
    "Use leftovers creatively to make new meals.",
    "Freeze excess food to preserve it for future use.",
    "Check expiration dates regularly and prioritize older items.",
    "Share excess food with friends, family, or local charities.",
    "Make a shopping list to avoid impulse purchases.",
    "Compost food scraps instead of throwing them away.",
    "Buy only what you need, especially for perishable items.",
  ];

  let currentTip = null;
  let spinning = false;

  const generateRandomTip = () => {
    if (spinning) return; // Prevent multiple clicks during spinning
    spinning = true;

    setTimeout(() => {
      const randomIndex = Math.floor(Math.random() * tips.length);
      currentTip = tips[randomIndex];
      spinning = false;
    }, 1000); // Simulate spinning delay
  };
</script>

{#if showModalTips}
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div class="modal-overlay" on:click={closeModalTips}>
    <div class="modal" on:click|stopPropagation>
      <button class="close-button" on:click={closeModalTips}>&times;</button>
      <h2>Spin to Get a Food-Saving Tip!</h2>
      <div class="game-container">
        <div class="spinner">
          {#if spinning}
            <p class="spinner-text">Spinning...</p>
          {:else if currentTip}
            <p class="tip-text">{currentTip}</p>
          {:else}
            <p class="tip-text">Press Spin to Get a Tip!</p>
          {/if}
        </div>
        <button class="spin-button" on:click={generateRandomTip}> Spin </button>
      </div>
    </div>
  </div>
{/if}

<style>
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 200;
  }

  .modal {
    background: white;
    padding: 2rem;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    max-width: 600px;
    width: 90%;
    position: relative;
    text-align: center;
  }

  .modal h2 {
    font-size: 1.5rem;
    color: #2ecc71;
    margin-bottom: 1.5rem;
  }

  .game-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1.5rem;
  }

  .spinner {
    width: 250px;
    height: 150px;
    display: flex;
    justify-content: center;
    align-items: center;
    background: #f9f9f9;
    border: 2px dashed #ccc;
    border-radius: 10px;
    padding: 1rem;
    position: relative;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  }

  .spinner-text {
    font-size: 1.2rem;
    color: #666;
    animation: spin 1s linear infinite;
  }

  .tip-text {
    font-size: 1rem;
    color: #333;
  }

  .spin-button {
    padding: 0.8rem 2rem;
    font-size: 1rem;
    font-weight: bold;
    color: white;
    background: #2ecc71;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: background 0.3s;
  }

  .spin-button:hover {
    background: #27ae60;
  }

  .close-button {
    background: transparent;
    border: none;
    font-size: 1.5rem;
    color: #999;
    position: absolute;
    top: 1rem;
    right: 1rem;
    cursor: pointer;
  }

  .close-button:hover {
    color: #333;
  }

  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }
</style>
