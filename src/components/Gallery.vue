<template>
   <div class="canvas" @click="$emit('open-modal', photo)">
      <img :src="photo.urls.regular" :alt="photo.alt_description" :title="photo.alt_description"/>
        <div class="overlay" :class="{visible: isVisible}" :title="photo.alt_description"></div>
          <div class="caption">
            <p>{{photo.user.first_name}} {{photo.user.last_name}}</p>
            <p>{{photo.user.location}}</p>
        </div>
    </div>
</template>

<script>
    export default {
      props: ['photo', 'isLoaded', 'isVisible']
  }
</script>


<style lang="scss" scoped>

$grid-height: 150px;
$abs: absolute;

  div.canvas{
      margin: 0;
      cursor: zoom-in;
      position: relative;
  
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
    opacity: 0;
    visibility: hidden;
    background: linear-gradient(transparent 50%, #000000);
    border-radius: 5px;
    transition: opacity 2s ease-out;
  &.visible{
    opacity: 1;
    visibility: visible;
  }
  }

  .caption{
    width: 100%;
    position: $abs;
    bottom: 0;
    left: 0;
    text-align: left;
    padding-left: 1.25rem;
    padding-bottom: 1.875rem;
    font-family: var(--buck-regular-font);

   & p:nth-child(1){
     font-family: var(--buck-med-font);
     font-size: 1rem;
     color: var(--photo-p1-color);
  }
   & p:nth-child(2){
    font-size: 0.875rem;
    color: var(--photo-p2-color);
    padding-top: 0.125rem;
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