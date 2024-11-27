<script>import "./app.css";
// import Header from "./components/Header.svelte";
// @ts-ignore
import Header from "./components/header.svelte";
// import Hero from "../components/Hero.svelte";
import DonationCounter from "./components/DonationCounter.svelte";
import Stats from "./components/stats.svelte";
import Parentview from "./components/parentview.svelte";
import nonu from '/nonu.mp4';
// import Stats2 from "../components/stats2.svelte";
</script>

<Header></Header>
<DonationCounter></DonationCounter>

<main>
  <!-- <h1>Welcome to FoodShare!</h1> -->
   <!-- <Stats2></Stats2>
  <Hero></Hero> -->
  <!-- <Parentview></Parentview> -->
  <!-- svelte-ignore a11y-media-has-caption -->
  <video  autoplay loop muted >
    <source src={nonu} type="video/mp4">
    Your browser does not support the video tag.
  
</main>
<Stats></Stats>

<style>
  main {
    padding: 2rem;
    font-family: Arial, sans-serif;
    text-align: center;
    color: #333;
  }
</style>
