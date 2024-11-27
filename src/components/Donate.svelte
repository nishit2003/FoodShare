<script>
  export let showModalDonateUs = false;
  export let closeModalDonateUs;

  const slogan = "Your Generosity Can Change Lives.";
  const description = `
    At FoodShare, every contribution matters. Your donation helps us reduce food waste 
    and provide meals to those in need. Together, we can create a sustainable and compassionate community.
  `;
</script>

{#if showModalDonateUs}
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div class="modal-overlay" on:click={closeModalDonateUs}>
    <div class="modal" on:click|stopPropagation>
      <button class="close-button" on:click={closeModalDonateUs}>&times;</button
      >
      <div class="modal-content">
        <h2>{slogan}</h2>
        <p class="description">{description}</p>
        <div class="cta-container">
          <button
            class="donate-button"
            on:click={() => alert("Thank you for donating!")}
          >
            Donate Now
          </button>
        </div>
        <img
          class="donate-image"
          src="https://www.capablewealth.com/wp-content/uploads/2019/12/Blog-Should-You-Donate-To-Charity-Now-Or-Wait-Until-you-Have-More-Money-Later.jpg"
          alt="Donate and make a difference"
        />
      </div>
    </div>
  </div>
{/if}

<style>
  /* Overlay */
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

  /* Modal */
  .modal {
    background: white;
    width: 80%;
    max-width: 700px;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    position: relative;
    text-align: center;
  }

  .modal-content {
    padding: 2rem;
  }

  .modal-content h2 {
    font-size: 2rem;
    font-weight: bold;
    color: #2ecc71;
    margin-bottom: 1rem;
  }

  .modal-content .description {
    font-size: 1rem;
    color: #555;
    line-height: 1.5;
    margin-bottom: 1.5rem;
  }

  /* Call-to-Action */
  .cta-container {
    margin: 1rem 0;
  }

  .donate-button {
    padding: 0.8rem 2rem;
    font-size: 1.2rem;
    font-weight: bold;
    color: white;
    background: #e74c3c;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: background 0.3s ease;
  }

  .donate-button:hover {
    background: #c0392b;
  }

  /* Image */
  .donate-image {
    width: 100%;
    height: 200px;
    object-fit: cover;
    margin-top: 1rem;
  }

  /* Close Button */
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

  @media (max-width: 768px) {
    .modal-content h2 {
      font-size: 1.5rem;
    }

    .donate-button {
      font-size: 1rem;
    }
  }
</style>
