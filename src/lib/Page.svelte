
{#each pagelist as p, i}
  <div class="page {p.isflip?'flip-animation':'flipback-animation'}" style="z-index: { p.isflip? p.no: 1};">
    <div class="face">{p.content}</div>
    <div class="back">{p.content + '背面' }</div>
  </div>  
{/each}


<script lang="ts">
  interface PageInfo {
    content?: string,
    img?: string,
    padding?: number,
    position?: string,
    isflip: boolean,
    [propName: string]: any;
  }

  export let pagelist:Array<PageInfo>;

</script>

<style>
  .page {
    position: absolute;
    top: 0;
    left: 0;
    width: 300px;
    height: 300px;
    border: 1px solid #1976D2;
    text-align: center;
    background-color: #fff;
    transform-origin: 0% 50%;
    -webkit-transform-origin: 0% 50%;
    -moz-transform-origin: 0% 50%;
    -ms-transform-origin: 0% 50%;
    -o-transform-origin: 0% 50%;
    transform-style: preserve-3d;
  }

  .face {
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: #fff;
    backface-visibility: hidden;
  }

  .back {
    position: absolute;
    width: 100%;
    height: 100%;
    background-color: #fff;
    transform: rotateY(180deg);
  }

  /*动画部分*/
  .flip-animation {
    animation: flipBook 3s;
    animation-fill-mode: forwards;
  }

  @keyframes flipBook {
    0% {
      -webkit-transform: rotateY(0deg);
      -ms-transform: rotateY(0deg);
      -o-transform: rotateY(0deg);
      transform: rotateY(0deg);
    }

    100% {
      -webkit-transform: rotateY(-180deg);
      -ms-transform: rotateY(-180deg);
      -o-transform: rotateY(-180deg);
      transform: rotateY(-180deg);
    }
  }

  .flipback-animation {
    animation: flipBookback 3s;
    animation-fill-mode: forwards;
  }

  @keyframes flipBookback {
    0% {
      -webkit-transform: rotateY(-180deg);
      -ms-transform: rotateY(-180deg);
      -o-transform: rotateY(-180deg);
      transform: rotateY(-180deg);
    }
    100% {
      -webkit-transform: rotateY(0deg);
      -ms-transform: rotateY(0deg);
      -o-transform: rotateY(0deg);
      transform: rotateY(0deg);
    }
  }

</style>