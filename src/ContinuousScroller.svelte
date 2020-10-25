<script>
  import {onMount} from 'svelte';
  import {gsap} from 'gsap';
  import {ScrollTrigger} from 'gsap/ScrollTrigger';

  export let sectionName;
  export let imgOriginWidth;
  export let imgOriginHeight;
  export let frameCount;
  export let imageUrl;
  export let imageType;
  export let scrollSpacing;

  gsap.registerPlugin(ScrollTrigger);

  onMount(() => {
    const canvas = document.getElementById('img-container');
    const context = canvas.getContext('2d');

    canvas.width = imgOriginWidth;
    canvas.height = imgOriginHeight;

    const currentFrame = (index) => `${imageUrl}-${index + 1}.${imageType}`;
    const images = [];
    const pinImages = {
      frame: 0
    };

    for (let i = 0; i < frameCount; i++) {
      const img = new Image();
      img.src = currentFrame(i);
      images.push(img);
    }

    gsap.to(pinImages, {
      frame: frameCount - 1,
      snap: 'frame',
      scrollTrigger: {
        trigger: '#section-' + sectionName,
        scrub: true,
        start: 'top+=338px center',
        end: `bottom+=${scrollSpacing}px center`,
        pin: true,
        pinSpacing: true,
        markers: true
      },
      onUpdate: render // use animation onUpdate instead of scrollTrigger's onUpdate
    });

    images[0].onload = render;

    function render() {
      context.clearRect(0, 0, canvas.width, canvas.height);
      context.drawImage(images[pinImages.frame], 0, 0);
    }

    setTimeout(() => {
      ScrollTrigger.refresh();
    }, 100);
  });
</script>

<section class="grid grid-cols-12 gap-x-4 grid-flow-row;" id="section-{sectionName}">
  <canvas class="w-4/6 sm:w-4/6 mt-4 mx-auto text-center col-start-1 col-end-13" id="img-container" />

  {#each [1, 2] as block}
    <p class="article-grid article-p">
      我們是因為喜歡研究數位敘事及資料新聞，而聚集在一起的夥伴，期待能夠透過不同的敘事方式，放大故事影響力。
      「融數」結合數位（Digital）、數據（Data）的概念，我們希望這個計畫能夠作為同好的聚集地，除了紀錄研究與學習的過程，也將持續分享創新想法。
    </p>
  {/each}
</section>
