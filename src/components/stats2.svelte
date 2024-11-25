<script>
    // No additional logic is needed for static content
    import one from '/one.png';
</script>

<style>
    .section {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        text-align: center;
        padding: 2rem;
        background-color: #ffffff;
        color: #333;
    }

    .headline {
        font-size: 1.5rem;
        font-weight: 500;
        color: #333;
        margin-bottom: 1rem;
    }

    .highlight {
        color: #68B648; /* Green color for emphasis */
        font-weight: bold;
    }

    .cta {
        font-size: 1.2rem;
        font-weight: bold;
        color: #68B648;
        text-transform: uppercase;
        margin-top: 1rem;
    }
</style>

<div class="section">
    <!-- Text Content -->
    <div class="headline">
        <span class="highlight">1 in 4</span> people in Hamilton County is struggling with food insecurity.
    </div>

    

    

    <div class="image-container">
        <img src="/one.png" alt="1 out of 4 people illustration" />
    </div>

    <!-- Call-to-Action -->
    <div class="cta">
        Join us at the table, and make sure no one goes hungry.
    </div>
</div>
