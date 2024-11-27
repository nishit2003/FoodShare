<script>
  export let showModalAbout = false;
  export let closeModalAbout;

  // About Us information
  const aboutUsInfo = {
    title: "About FoodShare",
    subtitle: "Hunger Relief NGO for the People of Ohio",
    description: `
      At FoodShare, we strive to reduce food waste and fight hunger in Ohio.
      By connecting individuals and businesses with surplus food to those in need,
      we aim to create a sustainable and compassionate community.
      Through innovative solutions like our donation platform and tips for reducing food waste,
      we empower everyone to make a difference.
    `,
    mission: "To ensure no food goes to waste and no one goes hungry.",
    vision: "A world where food is abundant, shared, and never wasted.",
    image: "/logo.png", // Replace with your actual image path
  };
</script>

{#if showModalAbout}
<!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div class="modal-overlay" on:click={closeModalAbout}>
    <div class="modal" on:click|stopPropagation>
      <button class="close-button" on:click={closeModalAbout}>&times;</button>
      <img class="banner-image" src={aboutUsInfo.image} alt="About FoodShare" />
      <div class="modal-content">
        <h2>{aboutUsInfo.title}</h2>
        <h3>{aboutUsInfo.subtitle}</h3>
        <p class="description">{aboutUsInfo.description}</p>
        <div class="extra-info">
          <div class="info-card">
            <h4>Our Mission</h4>
            <p>{aboutUsInfo.mission}</p>
          </div>
          <div class="info-card">
            <h4>Our Vision</h4>
            <p>{aboutUsInfo.vision}</p>
          </div>
        </div>
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
    max-width: 900px;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    overflow: hidden;
    display: flex;
    flex-direction: column;
    position: relative;
  }

  .banner-image {
    width: 100%;
    height: 200px;
    object-fit: cover;
  }

  .modal-content {
    padding: 1.5rem;
  }

  .modal-content h2 {
    font-size: 2rem;
    font-weight: bold;
    color: #2ecc71;
    margin-bottom: 0.5rem;
    text-align: center;
  }

  .modal-content h3 {
    font-size: 1.2rem;
    font-weight: 500;
    color: #555;
    margin-bottom: 1rem;
    text-align: center;
  }

  .modal-content .description {
    font-size: 1rem;
    color: #333;
    margin-bottom: 1.5rem;
    line-height: 1.5;
    text-align: center;
  }

  .extra-info {
    display: flex;
    gap: 1rem;
    justify-content: center;
  }

  .info-card {
    background: #f9f9f9;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    padding: 1rem;
    text-align: center;
    flex: 1;
    max-width: 45%;
  }

  .info-card h4 {
    font-size: 1.2rem;
    font-weight: bold;
    color: #2ecc71;
    margin-bottom: 0.5rem;
  }

  .info-card p {
    font-size: 0.95rem;
    color: #555;
    line-height: 1.4;
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
    z-index: 10;
  }

  .close-button:hover {
    color: #333;
  }

  @media (max-width: 768px) {
    .extra-info {
      flex-direction: column;
    }

    .info-card {
      max-width: 100%;
    }
  }
</style>
