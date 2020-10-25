<script>
  import Nav from './shared/Nav.svelte';
  import Footer from './shared/Footer.svelte';
  import ContinuousScroller from './ContinuousScroller.svelte';
</script>

<style>
</style>

<main>
  <Nav />
  <article class="article-grid-template mx-4" id="trigger-container">
    <h1 class="article-grid text-center">數位敘事滑起來！</h1>
    <p class="article-grid article-p">
      我們是因為喜歡研究數位敘事及資料新聞，而聚集在一起的夥伴，期待能夠透過不同的敘事方式，放大故事影響力。
      「融數」結合數位（Digital）、數據（Data）的概念，我們希望這個計畫能夠作為同好的聚集地，除了紀錄研究與學習的過程，也將持續分享創新想法。
    </p>
    <h4 class="article-grid article-h4">滾動數位敘事的現在與未來</h4>
    <p class="article-grid article-p">Hmmm ... 來用 gapminder 資料實作一下靜態滾動唄！</p>

    <section class="article-grid" id="section-2">
      {#each [1, 2] as block}
        <p class="article-p">
          我們是因為喜歡研究數位敘事及資料新聞，而聚集在一起的夥伴，期待能夠透過不同的敘事方式，放大故事影響力。
          「融數」結合數位（Digital）、數據（Data）的概念，我們希望這個計畫能夠作為同好的聚集地，除了紀錄研究與學習的過程，也將持續分享創新想法。
        </p>
      {/each}
    </section>
    <div class="col-start-1 col-end-13">
      <ContinuousScroller
        sectionName="gapminder"
        imgOriginWidth="1158"
        imgOriginHeight="1158"
        frameCount="12"
        imageUrl="assets/gapminder/gapminder"
        imageType="png"
        scrollSpacing="1000" />
    </div>
  </article>
  <Footer />
</main>
