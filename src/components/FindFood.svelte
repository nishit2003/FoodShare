<script>
  export let showModalFood = false;
  export let closeModalFood;

  // Sample food data
  const foodItems = [
    {
      id: 1,
      image: "/images/pizza.jpg",
      title: "Pizza",
      ingredients: ["Flour", "Cheese", "Tomato Sauce"],
    },
    {
      id: 2,
      image: "/images/salad.jpg",
      title: "Salad",
      ingredients: ["Lettuce", "Tomatoes", "Cucumbers"],
    },
    {
      id: 3,
      image: "/images/sandwich.jpg",
      title: "Sandwich",
      ingredients: ["Bread", "Lettuce", "Chicken"],
    },
    {
      id: 4,
      image: "/images/pasta.jpg",
      title: "Pasta",
      ingredients: ["Pasta", "Cheese", "Basil"],
    },
    {
      id: 5,
      image: "/images/soup.jpg",
      title: "Soup",
      ingredients: ["Carrots", "Onions", "Celery"],
    },
    {
      id: 6,
      image: "/images/burger.jpg",
      title: "Burger",
      ingredients: ["Buns", "Beef Patty", "Lettuce"],
    },
    {
      id: 7,
      image: "/images/curry.jpg",
      title: "Curry",
      ingredients: ["Chicken", "Spices", "Rice"],
    },
    {
      id: 8,
      image: "/images/dessert.jpg",
      title: "Dessert",
      ingredients: ["Cream", "Sugar", "Berries"],
    },
    {
      id: 9,
      image: "/images/pie.jpg",
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
      <h2>Find Food</h2>

      <!-- Food Grid -->
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

      <!-- Ingredients Modal -->
      {#if selectedIngredients}
        <div class="ingredients-modal" on:click={() => (selectedIngredients = null)}>
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
    position: relative;
    overflow-y: auto;
  }

  .modal h2 {
    font-size: 1.5rem;
    color: #2ecc71;
    margin-bottom: 1rem;
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
  }

  .grid-item {
    background: #f9f9f9;
    border: 1px solid #ccc;
    border-radius: 8px;
    padding: 1rem;
    text-align: center;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  }

  .grid-item img {
    width: 100%;
    height: 150px;
    object-fit: cover;
    border-radius: 8px;
    margin-bottom: 1rem;
  }

  .grid-item h3 {
    font-size: 1.2rem;
    color: #333;
    margin-bottom: 0.5rem;
  }

  .grid-item button {
    display: block;
    width: 100%;
    margin-bottom: 0.5rem;
    padding: 0.5rem;
    font-size: 0.9rem;
    border: none;
    border-radius: 5px;
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
