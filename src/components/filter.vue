<template>
   <section id="store" class="store py-5">
    <div class="container">
      <!-- section title -->
      <div class="row">
        <div class="col-10 mx-auto col-sm-6 text-center">
          <h1 class="text-capitalize">our <strong class="banner-title ">store</strong></h1>
        </div>
      </div>
      <!-- end of section title -->
      <!--filter buttons -->
      <div class="row">
        <div class=" col-lg-8 mx-auto d-flex justify-content-around my-2 sortBtn flex-wrap">
          <a href="#" class="btn btn-outline-secondary btn-black text-uppercase filter-btn m-2" v-on:click.prevent="filterItems" ref="all" data-filter="all"> all</a>
          <a href="#" class="btn btn-outline-secondary btn-black text-uppercase filter-btn m-2" v-on:click.prevent="filterItems" ref="cakes" data-filter="cakes">cakes</a>
          <a href="#" class="btn btn-outline-secondary btn-black text-uppercase filter-btn m-2" v-on:click.prevent="filterItems" ref="cup" data-filter="cupcakes">cupcakes</a>
          <a href="#" class="btn btn-outline-secondary btn-black text-uppercase filter-btn m-2" v-on:click.prevent="filterItems" ref="sweet" data-filter="sweets">sweets</a>
          <a href="#" class="btn btn-outline-secondary btn-black text-uppercase filter-btn m-2" v-on:click.prevent="filterItems" ref="dough" data-filter="doughnuts">doughnuts</a>
        </div>
      </div>
      <!-- search box -->
      <div class="row">

        <div class="col-10 mx-auto col-md-6">
          <form>
            <div class="input-group mb-3">
              <div class="input-group-prepend ">
                <span class="input-group-text search-box" id="search-icon"><i class="fas fa-search"></i></span>
              </div>
              <input type="text" class="form-control" placeholder='item....' id="search-item">
            </div>

          </form>
        </div>
      </div>
      <!--end of filter buttons -->
      <!-- store  items-->
      <div class="row" id="store-items">
        <!-- single item -->
        <div class="col-10 col-sm-6 col-lg-4 mx-auto my-3 store-item " data-item="sweets" v-for="(item, i) in items" :key="i" ref="snack">
          <div class="card ">
            <div class="img-container">
              <img :src="('/img/' + item.pic)" class="card-img-top store-img" alt="">
              <span class="store-item-icon">
                <i class="fas fa-shopping-cart"></i>
              </span>
            </div>
            <div class="card-body">
              <div class="card-text d-flex justify-content-between text-capitalize">
                <h5 id="store-item-name">{{item.name}}</h5>
                <h5 class="store-item-value">$ <strong id="store-item-price" class="font-weight-bold">{{item.price}}</strong></h5>

              </div>
            </div>
          </div>
          </div>
          <!-- end of card-->
        </div>
        <!--end of single store item-->
        <!-- single item -->
       
    </div>
  </section>
</template>

<script>


export default {
  data(){
    return{
      items:[
        {
          pic:"sweets-1.jpeg",
          name:"Sweet Item",
          price:5
        },
        {
          pic:"cupcake-1.jpeg",
          name:"Cupcake Item",
          price:5
        },
        {
          pic:"cake-1.jpeg",
          name:"Cake Item",
          price:5
        },
        {
          pic:"doughnut-1.jpeg",
          name:"Doughnut Item",
          price:5
        },
          {
          pic:"sweets-2.jpeg",
          name:"Sweet Item",
          price:10
        },
        {
          pic:"cupcake-2.jpeg",
          name:"Cupcake Item",
          price:10
        },
        {
          pic:"cake-2.jpeg",
          name:"Cake Item",
          price:10
        },
        {
          pic:"doughnut-2.jpeg",
          name:"Doughnut Item",
          price:10
        },
        {
          pic: "sweets-3.jpeg",
          name:"Sweet Item",
          price:15
        },
        {
          pic:"cupcake-3.jpeg",
          name:"Cupcake Item",
          price:15
        },
        {
          pic:"cake-3.jpeg",
          name:"Cake Item",
          price:15
        },
        {
          pic:"doughnut-3.jpeg",
          name:"Doughnut Item",
          price:15
        }
      ],
      display:'none'
    }
  },
  methods:{
    filterItems(e){
      let take = e.target.dataset.filter;
      console.log("i am filter");
      this.$refs.snack.forEach((item) =>{
        if(take === this.$refs.all){
          item.style.display = 'block'
          console.log("i am all")
        } else {
          if(take === this.$refs.cake){
            item.style.display = 'block'
            console.log("i am cake")
          }
        }
      })
      }
    }
  }
  // directives:{
  //   'register':{
  //     bind(el, binding){
  //       const { value } = binding;
  //       el.dataset.filter = value;
  //     }
  //   }
  // }
</script>

<style>

</style>

