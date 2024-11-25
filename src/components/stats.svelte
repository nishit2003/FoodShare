<script>
    // Define the statistics
    const stats = [
        { icon: "👨‍👩‍👧", value: "129,000+", label: "Food Insecure Served Annually" },
        { icon: "🤝", value: "200+", label: "Agency Partners & Pantries" },
        { icon: "🍽️", value: "15+", label: "Meals Provided with as less as $6" }
    ];
</script>

<style>
    .section {
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #3d405b; /* Green background */
        color: white;
        padding: 2rem 3rem;
        border-radius: 10px;
    }

    .text-block {
        flex: 1;
        font-size: 1.5rem;
        line-height: 2rem;
        font-weight: 500;
        max-width: 400px;
    }

    .stats {
        flex: 2;
        display: flex;
        justify-content: space-evenly;
        align-items: center;
    }

    .stat {
        text-align: center;
    }

    .icon {
        font-size: 2.5rem;
        margin-bottom: 0.5rem;
    }

    .value {
        font-size: 2rem;
        font-weight: bold;
        margin-bottom: 0.3rem;
    }

    .label {
        font-size: 1rem;
        font-weight: 500;
    }

    .subscribe {
        position: absolute;
        top: 50%;
        right: -1.5rem;
        transform: translateY(-50%);
        background-color: #FFA500; /* Orange */
        color: white;
        font-size: 1rem;
        font-weight: bold;
        padding: 0.5rem 1rem;
        border-radius: 10px 0 0 10px;
        writing-mode: vertical-lr;
        text-align: center;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
        cursor: pointer;
    }
</style>

<div class="section">
    <!-- Left Text Block -->
    <div class="text-block">
        We are a member of the <strong>Feeding Ohio</strong> network, the state's
        largest hunger-relief organization.
    </div>

    <!-- Statistics Section -->
    <div class="stats">
        {#each stats as stat}
            <div class="stat">
                <div class="icon">{stat.icon}</div>
                <div class="value">{stat.value}</div>
                <div class="label">{stat.label}</div>
            </div>
        {/each}
    </div>

    <!-- Subscribe Button -->
    <div class="subscribe">Subscribe</div>
</div>
