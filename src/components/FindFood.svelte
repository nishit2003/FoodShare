<script>
  export let showModalFood = false;
  export let closeModalFood;
  import Hero from "./hero.svelte";

  // Sample food data
  const foodItems = [
    {
      id: 1,
      image: "https://www.foodandwine.com/thmb/4qg95tjf0mgdHqez5OLLYc0PNT4=/750x0/filters:no_upscale():max_bytes(150000):strip_icc():format(webp)/classic-cheese-pizza-FT-RECIPE0422-31a2c938fc2546c9a07b7011658cfd05.jpg", 
      title: "Pizza",
      ingredients: ["Flour", "Cheese", "Tomato Sauce"],
    },
    {
      id: 2,
      image: "https://cdn.loveandlemons.com/wp-content/uploads/2021/04/green-salad.jpg",
      title: "Salad",
      ingredients: ["Lettuce", "Tomatoes", "Cucumbers"],
    },
    {
      id: 3,
      image: "https://www.sargento.com/assets/Uploads/Recipe/Image/Sargento11501__FillWzExNzAsNTgzXQ.jpg",
      title: "Sandwich",
      ingredients: ["Bread", "Lettuce", "Chicken"],
    },
    {
      id: 4,
      image: "https://assets.epicurious.com/photos/5988e3458e3ab375fe3c0caf/1:1/w_3607,h_3607,c_limit/How-to-Make-Chicken-Alfredo-Pasta-hero-02082017.jpg",
      title: "Pasta",
      ingredients: ["Pasta", "Cheese", "Basil"],
    },
    {
      id: 5,
      image: "https://www.connoisseurusveg.com/wp-content/uploads/2024/02/vegetable-noodle-soup-sq.jpg",
      title: "Soup",
      ingredients: ["Carrots", "Onions", "Celery"],
    },
    {
      id: 6,
      image: "https://www.thespruceeats.com/thmb/UpVWAcHnFEe_KvQpYsR1a7U-WY0=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc()/SES-your-best-grilled-burger-recipe-7511041-hero-C-c5080fa5f97c4c2b908968527f8a851b.jpg",
      title: "Burger",
      ingredients: ["Buns", "Beef Patty", "Lettuce"],
    },
    {
      id: 7,
      image: "https://saltedmint.com/wp-content/uploads/2024/01/Simple-Thai-yellow-chicken-curry.jpg",
      title: "Curry",
      ingredients: ["Chicken", "Spices", "Rice"],
    },
    {
      id: 8,
      image: "https://chopnotch.com/wp-content/uploads/2020/11/Panna-Cotta-1.jpg",
      title: "Dessert",
      ingredients: ["Cream", "Sugar", "Berries"],
    },
    {
      id: 9,
      image: "https://www.allrecipes.com/thmb/ITzMWta04gWy7ri2zIWFYfMvr54=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc()/AR-76296-Meat-Pie-DDMFS-4x3-beauty-f987781548f14bfcb0cb282f598e4e60.jpg",
      title: "Pie",
      ingredients: ["Pie Crust", "Apples", "Cinnamon"],
    },
  ];

  // State for showing ingredients
  let selectedIngredients = null;

  // Function to show ingredients for a specific food item
  const showIngredients = (ingredients) => {
    selectedIngredients = ingredients;
  };

  // Function to reserve an item
  const reserveItem = (title) => {
    alert(`You reserved: ${title}`);
  };
</script>

{#if showModalFood}
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <!-- svelte-ignore a11y-no-static-element-interactions -->
  <div class="modal-overlay" on:click={closeModalFood}>
    <div class="modal" on:click|stopPropagation>
      <button class="close-button" on:click={closeModalFood}>&times;</button>
      <div class="content">
        <Hero />
        <div class="grid">
          {#each foodItems as item}
            <div class="grid-item">
              <img src={item.image} alt={item.title} />
              <h3>{item.title}</h3>
              <button on:click={() => showIngredients(item.ingredients)}>
                See Ingredients
              </button>
              <button on:click={() => reserveItem(item.title)}>Reserve</button>
            </div>
          {/each}
        </div>
      </div>

      <!-- Ingredients Modal -->
      {#if selectedIngredients}
        <div
          class="ingredients-modal"
          on:click={() => (selectedIngredients = null)}
        >
          <div class="ingredients-content" on:click|stopPropagation>
            <button
              class="close-button"
              on:click={() => (selectedIngredients = null)}
            >
              &times;
            </button>
            <h3>Ingredients</h3>
            <ul>
              {#each selectedIngredients as ingredient}
                <li>{ingredient}</li>
              {/each}
            </ul>
          </div>
        </div>
      {/if}
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
    max-width: 900px;
    width: 90%;
    height: 90%;
    position: relative;
    overflow-y: auto;
  }

  .content {
    display: flex;
    /* gap: 1rem; */
  }

  /* .hero {
    /* flex: 1; */
    /* background: #f9f9f9;
    padding: 1rem;
    border-radius: 8px;
    text-align: center; */
  /* } */ 

  .grid {
    flex: 1;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 0.5rem; /* Reduce gap between grid items */
    height: 100%; /* Constrain grid height */
    overflow-y: auto; /* Allow scrolling only if necessary */
  }

  .grid-item {
    background: #f9f9f9;
    border: 1px solid #ccc;
    border-radius: 8px;
    padding: 0.5rem; /* Reduce padding to save space */
    text-align: center;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }

  .grid-item img {
    width: 100%;
    height: 100px; /* Reduce image height */
    object-fit: cover;
    border-radius: 8px;
    margin-bottom: 0.5rem;
  }

  .grid-item h3 {
    font-size: 1rem; /* Reduce font size */
    color: #333;
    margin-bottom: 0.3rem;
  }

  .grid-item button {
    padding: 0.3rem; /* Reduce button padding */
    margin-bottom: 3px;
    font-size: 0.8rem; /* Reduce font size */
    border-radius: 4px;
    cursor: pointer;
    background: #2ecc71;
    color: white;
    transition: background 0.3s;
  }

  .grid-item button:hover {
    background: #27ae60;
  }

  .ingredients-modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.7);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 300;
  }

  .ingredients-content {
    background: white;
    padding: 2rem;
    border-radius: 10px;
    text-align: center;
    width: 400px;
    position: relative;
  }

  .ingredients-content h3 {
    margin-bottom: 1rem;
    color: #2ecc71;
  }

  .ingredients-content ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .ingredients-content li {
    margin: 0.5rem 0;
    font-size: 1rem;
    color: #333;
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
</style>
