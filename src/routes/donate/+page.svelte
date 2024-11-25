<script>
    // Add logic if needed
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

    .container {
        padding: 2rem;
        text-align: center;
    }

    h1 {
        font-size: 2.5rem;
        color: #2ecc71; /* Match the theme of your header */
    }

    p {
        font-size: 1.2rem;
        color: #555;
    }

    .button {
        display: inline-block;
        margin-top: 1.5rem;
        padding: 0.8rem 1.5rem;
        font-size: 1rem;
        color: white;
        background-color: #2ecc71;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        text-decoration: none;
    }

    .button:hover {
        background-color: #27ae60;
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
            <li><a href="/donate">Donate Food</a></li>
            <li><a href="/find">Find Food</a></li>
            <li><a href="/tips">Tips</a></li>
            <li><a href="/about">About</a></li>
        </ul>
    </nav>
</header>

<div class="container">
    <h1>Donate Food</h1>
    <p>
        Thank you for your generosity! Your donations make a real difference
        in fighting hunger.
    </p>
    <a class="button" href="/">Go Back to Home</a>
</div>
