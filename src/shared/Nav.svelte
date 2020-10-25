<script>
  import SocialBox from './SocialBox.svelte';
</script>

<style>
  img {
    width: 220px;
  }
</style>

<nav class="nav">
  <div class="inline-block">
    <a href="https://medium.com/dd-story-hub/">
      <figure class="ml-2">
        <img
          style="width: 120px"
          src="assets/DD-regular-logo-text.svg"
          alt="DD Story Hub logo" />
      </figure>
    </a>
  </div>
  <div class="inline-block">
    <SocialBox
      shareUrl="www.google.com"
      tnlPageId="139265"
      iconColor="#4e4948" />
  </div>
</nav>
