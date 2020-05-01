<template>
  <section id="store" class="store py-5">
    <div class="container">
      <!-- section title -->
      <div class="row">
        <div class="col-10 mx-auto col-sm-6 text-center">
          <h1 class="text-capitalize">
            our
            <strong class="banner-title">store</strong>
          </h1>
        </div>
      </div>
      <!-- end of section title -->
      <!--filter buttons -->
      <div class="row">
        <div class="col-lg-8 mx-auto d-flex justify-content-around my-2 sortBtn flex-wrap">
          <a
            href="#"
            class="btn btn-outline-secondary btn-black text-uppercase filter-btn m-2"
            v-on:click.prevent="filterItems()"
          >all</a>
          <a
            href="#"
            class="btn btn-outline-secondary btn-black text-uppercase filter-btn m-2"
            v-on:click.prevent="filterItems('cake')"
          >cakes</a>
          <a
            href="#"
            class="btn btn-outline-secondary btn-black text-uppercase filter-btn m-2"
            v-on:click.prevent="filterItems('cup')"
          >cupcakes</a>
          <a
            href="#"
            class="btn btn-outline-secondary btn-black text-uppercase filter-btn m-2"
            v-on:click.prevent="filterItems('sweet')"
          >sweets</a>
          <a
            href="#"
            class="btn btn-outline-secondary btn-black text-uppercase filter-btn m-2"
            v-on:click.prevent="filterItems('dough')"
          >doughnuts</a>
        </div>
      </div>
      <!-- search box -->
      <div class="row">
        <div class="col-10 mx-auto col-md-6">
          <form>
            <div class="input-group mb-3">
              <div class="input-group-prepend">
                <span class="input-group-text search-box" id="search-icon">
                  <i class="fas fa-search"></i>
                </span>
              </div>
              <input type="text" class="form-control" placeholder="item...." id="search-item"  @input="filterItems2()" v-model="select"/>
            </div>
          </form>
        </div>
      </div>
      <!--end of filter buttons -->
      <!-- store  items-->
      <div class="row" id="store-items">
        <!-- single item -->
        <div
          class="col-10 col-sm-6 col-lg-4 mx-auto my-3 store-item"
          data-item="sweets"
          v-for="(item, i) in filteredItems"
          :key="i"
          ref="snack"
        >
          <div class="card">
            <div class="img-container">
              <img :src="('/img/' + item.pic)" class="card-img-top store-img" alt />
              <span class="store-item-icon">
                <i class="fas fa-shopping-cart"></i>
              </span>
            </div>
            <div class="card-body">
              <div class="card-text d-flex justify-content-between text-capitalize">
                <h5 id="store-item-name">{{item.name}}</h5>
                <h5 class="store-item-value">
                  $
                  <strong id="store-item-price" class="font-weight-bold">{{item.price}}</strong>
                </h5>
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
          price:5,
          category:"sweet"
        },
        {
          pic:"cupcake-1.jpeg",
          name:"Cupcake Item",
          price:5,
          category:"cup"
          },
        {
          pic:"cake-1.jpeg",
          name:"Cake Item",
          price:5,
          category:"cake"
          },
        {
          pic:"doughnut-1.jpeg",
          name:"Doughnut Item",
          price:5,
          category:"dough"
          },
          {
          pic:"sweets-2.jpeg",
          name:"Sweet Item",
          price:10,
          category:"sweet"
        },
        {
          pic:"cupcake-2.jpeg",
          name:"Cupcake Item",
          price:10,
          category:"cup"
        },
        {
          pic:"cake-2.jpeg",
          name:"Cake Item",
          price:10,
          category:"cake"
        },
        {
          pic:"doughnut-2.jpeg",
          name:"Doughnut Item",
          price:10,
          category:"dough"
        },
        {
          pic: "sweets-3.jpeg",
          name:"Sweet Item",
          price:15,
          category:"sweet"
        },
        {
          pic:"cupcake-3.jpeg",
          name:"Cupcake Item",
          price:15,
          category:"cup"
        },
        {
          pic:"cake-3.jpeg",
          name:"Cake Item",
          price:15,
          category:"cake"
        },
        {
          pic:"doughnut-3.jpeg",
          name:"Doughnut Item",
          price:15,
          category:"dough"
        }
      ],
      filteredItems:[],
      select:''
    }
  },
  methods:{
    filterItems(category){
      this.filteredItems = this.items
      const result = this.filteredItems.filter((e) => {
       return e.category === category
     })
     if(result.length > 0){
       this.filteredItems = result
     }else {
       this.filteredItems = this.items
     }
  },
  filterItems2(){
      this.filteredItems = this.items
      const result = this.filteredItems.filter((e) => {
       return e.name.toLowerCase().includes(this.select)
     })
     if(result.length > 0){
       this.filteredItems = result
     }else {
       this.filteredItems = this.items
     }
  }
  },
  mounted(){
    this.filteredItems = this.items
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

