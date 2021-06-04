<div class="book">
  <Page pagelist={pages} ></Page>
</div>
<button on:click={last}>上一页</button>
<button on:click={flip}>下一页</button>

<script lang="ts">
  import Page from './Page.svelte'
  let pages = [
    {
      'content': '1',
      'img': '',
      'padding': 10,
      'position': 'center',
      'no': 1,
      'isflip': false
    },
    {
      'content': '2',
      'img': '',
      'padding': 10,
      'position': 'center',
      'no': 2,
      'isflip': false
    },
    {
      'content': '3',
      'img': '',
      'padding': 10,
      'position': 'center',
      'no': 3,
      'isflip': false
    },
    {
      'content': '4',
      'img': '',
      'padding': 10,
      'position': 'center',
      'no': 4,
      'isflip': false
    },
    {
      'content': '5',
      'img': '',
      'padding': 10,
      'position': 'center',
      'no': 5,
      'isflip': false
    },
    {
      'content': '6',
      'img': '',
      'padding': 10,
      'position': 'center',
      'no': 6,
      'isflip': false
    }
  ].sort((a,b)=>{
    return b.no - a.no
  })
  let pageindex = -1
  let flip = () => {
    if(pageindex + 1 != pages.length) {
      pageindex ++
      if(pageindex>-1) {
        let i = pages.length - (1 + pageindex)
        pages[i].isflip = true
      }
    }
  }
  let last = () => {
    pageindex --
    if(pageindex>-1) {
      let i = pages.length - 2 - pageindex
      console.log(i);
      
      pages[i].isflip = false
    } else if(pageindex === -1) {
      pages[pages.length-1].isflip = false
    }
  }
  
</script>

<style>
  .book {
    width: 300px;
    height: 300px;
    position: absolute;
    top: 20%;
    left: 40%;
    transform: rotateX(30deg);
    /*维持3D效果：即显示出rotateZ轴的效果*/
    -webkit-transform-style: preserve-3d;
    -moz-transform-style: preserve-3d;
    -ms-transform-style: preserve-3d;
    transform-style: preserve-3d;
    box-shadow: 3px 3px 2px 2px #dad6d6;
    transform: rotateX(15deg);
  }
</style>