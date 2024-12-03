<script>
  export let showModal = false;
  export let closeModal;

  import Stats2 from "./stats2.svelte";

  // Array to hold food items
  let foodItems = [{ name: "", price: "" }];

  // Function to add a new food item
  const addFoodItem = () => {
    foodItems = [...foodItems, { name: "", price: "" }];
  };

  // Function to remove a specific food item
  const removeFoodItem = (index) => {
    foodItems = foodItems.filter((_, i) => i !== index);
  };

  // States for sub-modals
  let showPickupModal = false;
  let showDropoffModal = false;

  // Pickup form fields
  let pickupDetails = {
    name: "",
    email: "",
    address: "",
  };

  // Function to handle dropoff selection
  const handleDropoff = () => {
    showDropoffModal = true;
  };

  // Function to handle pickup selection
  const handlePickup = () => {
    showPickupModal = true;
  };

  // Function to close sub-modals
  const closePickupModal = () => {
    showPickupModal = false;
  };
  const closeDropoffModal = () => {
    showDropoffModal = false;
  };

  // Confirmation
  let showConfirmation = false;

  const submitForm = () => {
    console.log("Submitted Food Items:", foodItems);
    closeModal(); // Close the modal after submission
    showConfirmation = true; // Show confirmation message
    setTimeout(() => {
      showConfirmation = false; // Hide confirmation animation after 3 seconds
    }, 3000);
  };
</script>

{#if showModal}
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div class="modal-overlay" on:click={closeModal}>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div class="modal" on:click|stopPropagation>
      <button class="close-button" on:click={closeModal}>&times;</button>
      <h2>Share Food</h2>
      <div class="horizontal-container">
        <!-- Donation Form -->
        <form on:submit|preventDefault={submitForm}>
          <!-- svelte-ignore a11y-label-has-associated-control -->
          <!-- svelte-ignore a11y-label-has-associated-control -->
          <label>Food Items</label>
          {#each foodItems as item, index}
            <div class="food-item">
              <input
                type="text"
                placeholder="Food Name"
                bind:value={item.name}
              />
              <input
                type="number"
                placeholder="Quantity"
                bind:value={item.qty}
              />

              <input
                type="number"
                placeholder="Price/Item"
                bind:value={item.price}
                min="0"
              />

              <button
                type="button"
                class="remove-button"
                on:click={() => removeFoodItem(index)}
                aria-label="Remove item"
              >
                &times;
              </button>
            </div>
          {/each}
          <button type="button" class="add-item-button" on:click={addFoodItem}>
            + Item
          </button>
          <h3>How would you like to share food?</h3>
          <div>
            <button
              type="button"
              class="add-item-button"
              on:click={handleDropoff}
            >
              Drop Off
            </button>
            <button
              type="button"
              class="add-item-button"
              on:click={handlePickup}
            >
              Pick Up
            </button>
          </div>
        </form>

        <!-- Stats Component -->
        <div class="stats-container">
          <Stats2 />
        </div>
      </div>
    </div>
  </div>
{/if}

<!-- Pickup Modal -->
<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
{#if showPickupModal}
  <div class="modal-overlay" on:click={closePickupModal}>
    <div class="modal3" on:click|stopPropagation>
      <button class="close-button" on:click={closePickupModal}>&times;</button>
      <h2>Schedule a Pickup</h2>
      <form on:submit|preventDefault={submitForm}>
        <label for="pickup-name">Your Name</label>
        <input
          type="text"
          id="pickup-name"
          placeholder="Enter your name"
          bind:value={pickupDetails.name}
        />

        <label for="pickup-email">Your Email</label>
        <input
          type="email"
          id="pickup-email"
          placeholder="Enter your email"
          bind:value={pickupDetails.email}
        />

        <label for="pickup-address">Pickup Address</label>
        <textarea
          id="pickup-address"
          rows="3"
          placeholder="Enter your address"
          bind:value={pickupDetails.address}
        ></textarea>

        <label for="pickup-date">Pickup Date</label>
        <input
          type="date"
          id="pickup-date"
          bind:value={pickupDetails.date}
        />

        <label for="pickup-time">Pickup Time</label>
        <input
          type="time"
          id="pickup-time"
          bind:value={pickupDetails.time}
        />

        <button type="submit">Submit</button>
      </form>
    </div>
  </div>
{/if}

<!-- Dropoff Modal -->
{#if showDropoffModal}
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div class="modal-overlay" on:click={closeDropoffModal}>
  <div class="modal2" on:click|stopPropagation>
    <button class="close-button" on:click={closeDropoffModal}>&times;</button>
    <h2>Drop Off Your Donation</h2>
    <p>
      Please drop off your food at:
      <br />
      <strong>FoodShare Donation Center</strong>
      <br />
      <strong>123 Community Drive, OHIO</strong>
    </p>

    <p>
      We are located at 1730 Race Street across from Findlay Market in
      Cincinnati, Ohio’s Over the Rhine neighborhood.
    </p>

    <p>
      When delivering food items, please come to our donation door in the back
      alley behind our building (map below). If you are heading south on Race,
      go past our building to the first drive on the left (parking lot).
    </p>

    <p>
      Make the next left onto the alley, and pull up to the green door on our
      yellow building.
    </p>

    <p>
      Ring the doorbell with the big green painted arrow next to it. Someone
      will help you unload, and you can be on your way!
    </p>

    <p>
      If you’d like to coordinate your donation with our current needs, contact
      Kathy Schickel, Director of Operations:
    </p>

    <p>
      <strong>Call:</strong> (602)- 815 3837 <br />
      <strong>Email:</strong> <a href="mailto:grovernt@mail.uc.edu">grovernt@mail.uc.edu</a>
    </p>
  </div>
</div>
{/if}

{#if showConfirmation}
  <div class="confirmation">🎉 Thank you for sharing Food!</div>
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
    color: black;
  }

  .modal {
    background: white;
    padding: 2rem;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    width: 1400px;
    max-width: 90%;
    position: relative;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }


  .modal2 {
    background: white;
    padding: 2rem;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    max-width: 600px;
    width: 90%;
    line-height: 1.6;
    font-size: 1rem;
    color: #333;
    position: relative;
    overflow-y: auto;
    max-height: 90vh;
  }

  .modal3 {
    background: white;
    padding: 2rem;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    max-width: 600px;
    width: 90%;
    line-height: 1.6;
    font-size: 1rem;
    color: #333;
    position: relative;
    overflow-y: auto;
    max-height: 90vh;
  }

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

  .modal3 h2 {
    font-size: 1.5rem;
    color: #2ecc71;
    margin-bottom: 1rem;
  }

  .modal3 label {
    display: block;
    font-weight: bold;
    margin-bottom: 0.5rem;
  }

  .modal3 input,
  .modal3 textarea {
    width: 100%;
    padding: 0.8rem;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 1rem;
    margin-bottom: 1rem;
  }

  .modal3 button {
    padding: 0.8rem;
    background: #2ecc71;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1rem;
    transition: background 0.3s;
  }

  .modal3 button:hover {
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


  .modal2 h2 {
    font-size: 1.5rem;
    color: #2ecc71;
    margin-bottom: 1rem;
  }

  .modal2 p {
    margin-bottom: 1rem;
    text-align: justify;
  }

  .modal2 a {
    color: #2ecc71;
    text-decoration: none;
  }

  .modal2 a:hover {
    text-decoration: underline;
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

  .modal h2 {
    margin-top: 0;
    font-size: 1.5rem;
    color: #2ecc71;
  }

  .horizontal-container {
    display: flex;
    gap: 2rem;
    align-items: flex-start;
  }

  .modal form {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .modal label {
    font-weight: bold;
    color: #333;
  }

  .food-item {
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .food-item input {
    flex: 1;
    padding: 0.8rem;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 1rem;
  }

  .remove-button {
    background: transparent;
    border: none;
    color: red;
    font-size: 1.5rem;
    cursor: pointer;
  }

  .confirmation {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #4caf50;
  color: #fff;
  padding: 1rem 2rem;
  border-radius: 8px;
  font-size: 1.2rem;
  text-align: center;
  z-index: 3002; /* Above the modal */
}

  .remove-button:hover {
    color: darkred;
  }

  .add-item-button {
    padding: 0.5rem 1rem;
    background: #2ecc71;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1rem;
    transition: background 0.3s;
  }

  .add-item-button:hover {
    background: #27ae60;
  }

  /* .modal button[type="submit"] {
    padding: 0.8rem;
    background: #2ecc71;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 1rem;
    transition: background 0.3s;
  }

  .modal button[type="submit"]:hover {
    background: #27ae60;
  } */

  .stats-container {
    flex: 1;
    min-width: 450px;
  }
</style>


<!-- {#if showConfirmation}
  <div class="confirmation">🎉 Thank you for donating Food!</div>
{/if} -->