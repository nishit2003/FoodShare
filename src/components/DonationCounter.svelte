<script>
    import { onDestroy, onMount } from "svelte";

    let donationCount = 10000; // Initial count
    let flipping = false; // Animation state
    let interval; // To store the interval reference

    // Increment the counter with animation
    const incrementCounter = () => {
        flipping = true;
        setTimeout(() => {
            donationCount += Math.floor(Math.random() * 10 + 1); // Random increment
            flipping = false;
        }, 500); // Match flip animation duration
    };

    // Setup interval on mount
    onMount(() => {
        interval = setInterval(incrementCounter, 6000); // 1-minute interval
    });

    // Cleanup interval on destroy
    onDestroy(() => {
        clearInterval(interval);
    });
</script>

<style>
    .counter-container {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 1rem;
        padding: 1rem 2rem;
        background: linear-gradient(135deg, #f4f4f9, #ffffff);
        border-radius: 10px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        font-family: Arial, sans-serif;
    }

    .card {
        position: relative;
        width: 3rem;
        height: 4rem;
        background: #81b29a;
        color: white;
        font-size: 2rem;
        font-weight: bold;
        border-radius: 5px;
        display: flex;
        justify-content: center;
        align-items: center;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        perspective: 1000px;
    }

    .flip {
        transform-style: preserve-3d;
        animation: flip 0.5s ease;
    }

    @keyframes flip {
        0% {
            transform: rotateX(0deg);
        }
        50% {
            transform: rotateX(90deg);
        }
        100% {
            transform: rotateX(0deg);
        }
    }

    .description {
        font-size: 1.5rem;
        font-weight: 500;
        color: #3d405b;
    }
</style>

<div class="counter-container">
   <p class="description">Meals donated so far</p>
    {#each donationCount.toString().split("") as num, index (index)}
        <div class="card {flipping ? 'flip' : ''}">
            {num}
        </div>
    {/each}
</div>

