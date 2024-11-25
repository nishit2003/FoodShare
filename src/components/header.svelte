<script>
    import DonateFood from "./DonateFood.svelte";
    import FindFood from "./FindFood.svelte";

    let showModal = false; // State for "Donate Food" modal
    let showModalFood = false; // State for "Find Food" modal

    // Functions to open and close the modals
    const openModal = () => (showModal = true);
    const closeModal = () => (showModal = false);

    const openModalFood = () => (showModalFood = true);
    const closeModalFood = () => (showModalFood = false);
</script>

<style>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem 2rem;
        background: linear-gradient(135deg, #f2cc8f, #27ae60); /* Stylish gradient */
        color: white;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        position: sticky;
        top: 0;
        z-index: 100;
    }

    .logo-container {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        gap: 0.2rem;
    }

    .logo {
        font-size: 1.8rem;
        font-weight: bold;
        text-transform: uppercase;
        letter-spacing: 2px;
        color: #ffffff;
    }

    .subtitle {
        font-size: 0.8rem;
        font-weight: normal;
        color: #ffffff;
        opacity: 0.9;
    }

    nav ul {
        list-style: none;
        display: flex;
        gap: 2rem;
        margin: 0;
        padding: 0;
    }

    nav ul li a {
        text-decoration: none;
        color: white;
        font-weight: 500;
        font-size: 1.2rem;
        transition: color 0.3s, transform 0.3s;
    }

    nav ul li a:hover {
        color: #f1c40f; /* Yellow hover effect */
        transform: translateY(-2px); /* Slight lift on hover */
    }
</style>

<header>
    <div class="logo-container">
        <div class="logo">FoodShare</div>
        <div class="subtitle">Hunger Relief NGO for OHIO</div>
    </div>
    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <!-- Trigger Donate Food modal -->
            <li>
                <!-- svelte-ignore a11y-invalid-attribute -->
                <a href="#" on:click={openModal}>Donate Food</a>
            </li>
            <!-- Trigger Find Food modal -->
            <li>
                <!-- svelte-ignore a11y-invalid-attribute -->
                <a href="#" on:click={openModalFood}>Find Food</a>
            </li>
            <li><a href="/tips">Tips</a></li>
            <li><a href="/about">About</a></li>
        </ul>
    </nav>

    <!-- Modals -->
    <DonateFood {showModal} {closeModal} />
    <FindFood {showModalFood} {closeModalFood} />
</header>
