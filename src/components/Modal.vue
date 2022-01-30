<template>
    <!-- <transition name="fade" appear> -->
    <div class="backdrop" @click.self="closeModal">
    <!-- </transition> -->
        <transition name="scale" appear>
        <div class="image-box">
            <img :src="photo.urls.regular" :alt="photo.alt_description" :title="photo.alt_description">
            <span @click="closeModal"><font-awesome-icon icon="times" /></span>
            <div class="image-desc">
                <h3>{{photo.user.first_name}} {{photo.user.last_name}}</h3>
                <p>{{photo.user.location}}</p>
            </div>
        </div>
        </transition>
    </div>
</template>
<script>
    // import { reactive, toRefs } from 'vue'
   export default{
    //    setup(props){
    //     const {img} = toRefs(props)
    //    }
    props: [ 'photo', 'activeClass'],
    methods:{
        closeModal(){
            this.$emit('close');
        }
    }
   }

</script>
<style lang="scss" scoped>

    $backdrop-color: #00000066; 
    $mw: 900px;
    $abs: absolute;
    $rel: relative;

    @mixin transform($prop){
    -webkit-transform: $prop;
    -ms-transform: $prop;
    transform: $prop;
}

    .backdrop{
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: $backdrop-color;
        display: flex;
        align-items: center;
        text-align: center;
        /* visibility: hidden;
        opacity: 0; */
        /* transform: scale(0); */
        /* transition: opacity .5s; */
        cursor: zoom-out;
    }
    /* .fade-enter-active,
    .fade-leave-active{
        transition: opacity 5s
    }
    .fade-enter,
    .fade-leave-to{
        opacity: 0;
    } */
    .scale-enter-active{
        animation: scale 0.5s;

    }
    .scale-leave-active{
        animation: scale 0.5s reverse;
    }
    @keyframes scale{
        0%{@include transform(scale(0))};
        100%{@include transform(scale(1))}
    }
    span{
        position: $abs;
        top: -30px;
        right: -80px;
        cursor: pointer;
        z-index: 10;
        color: #c2c2c4;
        padding: 0.3125rem;
        transition: all .3s, color .3s .3s;
  
    &:hover{
        @include transform(rotate(360deg));
        color: rgb(115, 9, 9);
    }
    }
    .image-box{
        position: $rel;
        margin: var(--base-margin-yA) var(--base-margin-xA);
        max-width: $mw;
        width: 100%;
        height: 90%;
        /* transition: transform .3s; */
        display: flex;
        justify-content: center;
        z-index: 2;
    }
    /* .backdrop.active image.box{
        transform: scale(1);
    } */
    img{
        width: 100%;
        // max-width: 900px;
        height: 100%;
        object-fit: cover;
        border-radius: 5px;
        cursor: default;
        position: $rel;
    }
    /* .backdrop.visible{
        visibility: visible;
        outline: none;
        cursor: default;
    } */
    .image-desc{
        position: $abs;
        bottom: 0;
        width: 100%;
        max-width: $mw;
        height: 100px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        flex-wrap: wrap;
        background: white;
        border-bottom-left-radius: 5px;
        border-bottom-right-radius: 5px;
        text-align: left;
        padding-left: 2.1875rem;
        padding-bottom: 0.625rem;
        margin: 0 auto;
        line-height: 20px;
        font-family: var(--buck-regular-font);

    & > h3{
        color: var(--modal-h3-color);
    }
    & p{
        color: --modal-p-color;
        font-size: 0.875rem;
        padding-top: 0.3125rem;
        font-family:  var(--buck-med-font);
    }
}

@media screen and (max-width: 1024px){
      span{
        right: 0;
      }
}
</style>