<template>
      <div class="canvas">
        <img  alt="" />
          <div class="overlay"></div>
            <div class="caption">
              <p>{{}} {{}}</p>
              <p>{{}}</p>
          </div>
    </div>
</template>
<script>
import {toRefs} from 'vue';
export default{
    setup(props){
        const {photo} = toRefs(props)

        return {photo}
    }
}

</script>
<style lang="scss" scoped>

$grid-height: 150px;
$rel: relative;
$abs: absolute;
$caption-pbg-color: #f5f5f5;
$caption-pbgalt-color: #f6f6f6;

  div.canvas{
      margin: var(--base-margin-yA);
      cursor: zoom-in;
      position: $rel;
      pointer-events: none;
      user-select: none;
  
      &:nth-child(2){
      grid-row: 1/span 2;
      grid-column: 2;
      height: 370px;
    }
    &:nth-child(3) {
        height: 330px;
    }
    &:nth-child(4) {
      grid-row: 2/4;
      height: 300px;
    }
    &:nth-child(5) {
      grid-row: 3;
      height: 370px;
      margin-top: -20px;
    }
    &:nth-child(6) {
      grid-column: 3/4;
      grid-row: 2/4;
      height: 340px;
      align-self: end;
    }
    &:nth-child(7){
      $grid-height: $grid-height * 2;
      height: $grid-height;
      grid-row: 4/5;
    }
    &:nth-child(8){
      height: 230px;
      grid-row: 5/4;
      grid-column: span 2;
      align-self: end;
    }
}
  img{
    width: 100%;
    height: 100%;
    object-fit: cover;
    background-color: var(--skeleton-bg-color);
    border-radius: 5px;
  }
  /* li:nth-child(2) img{
    grid-row: span 2; 
    grid-column: span 2;
  } */
 

  .overlay{
    position: $abs;
    bottom: 0;
    width: 100%;
    height: 100%;
    // background-blend-mode: lighten;
    background-color: var(--skeleton-o-color);
    border-radius: 5px;
    animation: pulsep 1s infinite;
    /* z-index: 1; */
  }

  .caption{
    width: 100%;
    position: $abs;
    bottom: 0;
    left: 0;
    text-align: left;
    padding-left: 1.25rem;
    padding-bottom: 1.825rem;

   & p:nth-child(1){
    // font-size: 14px;
    // color: white;
    height: 16px;
    width: 150px;
    background-color: $caption-pbg-color;
    animation: pulse 1s infinite;
  }
   & p:nth-child(2){
    // font-size: 12px;
    // // color: #d6d3d3;
    height: 16px;
    width: 100px;
    margin-top: 0.3125rem;
    background-color: $caption-pbg-color;
    animation: pulse 1s infinite;
  }
  @keyframes pulse{
      0%{background-color: var(--skeleton-o-color)};
      50%{background-color: var(--skeleton-alt-color)};
      100%{background-color: var(--skeleton-o-color)};
  }
  @keyframes pulsep{
      0%{background-color: $caption-pbg-color};
      50%{background-color: $caption-pbgalt-color};
      100%{background-color: $caption-pbg-color};
  }
  }

  @media screen and (max-width: 768px){
    div.canvas{
      grid-row: auto !important;
      grid-column: auto !important;
      height: 350px !important;
    }
  }
</style>