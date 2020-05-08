<template>
  <div>
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
                <input
                  type="text"
                  class="form-control"
                  placeholder="item...."
                  id="search-item"
                  @input="filterItems2()"
                  v-model="select"
                />
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
            @click="choose(i)"
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

    <!-- modal -->

    <div class="container-fluid">
      <div class="row lightbox-container align-items-center" v-if="show">
        <div class="col-10 col-md-10 mx-auto text-right lightbox-holder">
          <span class="lightbox-close">
            <i class="fas fa-window-close" @click="close()"></i>
          </span>
          <div
            class="lightbox-item"
            style="background-image:url('/img/cake-1.jpeg')"
            :style="{backgroundImage:`url('/img/${backgroundImage}')`}"
          ></div>
          <span class="lightbox-control btnLeft">
            <i class="fas fa-caret-left" @click="left()"></i>
          </span>
          <span class="lightbox-control btnRight">
            <i class="fas fa-caret-right" @click="right()"></i>
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          pic: "sweets-1.jpeg",
          name: "Sweet Item",
          price: 5,
          category: "sweet"
        },
        {
          pic: "cupcake-1.jpeg",
          name: "Cupcake Item",
          price: 5,
          category: "cup"
        },
        {
          pic: "cake-1.jpeg",
          name: "Cake Item",
          price: 5,
          category: "cake"
        },
        {
          pic: "doughnut-1.jpeg",
          name: "Doughnut Item",
          price: 5,
          category: "dough"
        },
        {
          pic: "sweets-2.jpeg",
          name: "Sweet Item",
          price: 10,
          category: "sweet"
        },
        {
          pic: "cupcake-2.jpeg",
          name: "Cupcake Item",
          price: 10,
          category: "cup"
        },
        {
          pic: "cake-2.jpeg",
          name: "Cake Item",
          price: 10,
          category: "cake"
        },
        {
          pic: "doughnut-2.jpeg",
          name: "Doughnut Item",
          price: 10,
          category: "dough"
        },
        {
          pic: "sweets-3.jpeg",
          name: "Sweet Item",
          price: 15,
          category: "sweet"
        },
        {
          pic: "cupcake-3.jpeg",
          name: "Cupcake Item",
          price: 15,
          category: "cup"
        },
        {
          pic: "cake-3.jpeg",
          name: "Cake Item",
          price: 15,
          category: "cake"
        },
        {
          pic: "doughnut-3.jpeg",
          name: "Doughnut Item",
          price: 15,
          category: "dough"
        }
      ],
      backgroundImage: "",
      show: false,
      filteredItems: [],
      select: "",
      counter: 0
    };
  },
  methods: {
    
    filterItems(gory) {
      this.filteredItems = this.items;
      const result = this.filteredItems.filter(e => {
        return e.category === gory;
      });
      if (result.length > 0) {
        this.filteredItems = result;
      } else {
        this.filteredItems = this.items;
      }
    },

    filterItems2() {
      this.filteredItems = this.items;
      const result = this.filteredItems.filter(e => {
        return e.name.toLowerCase().includes(this.select);
      });
      if (result.length > 0) {
        this.filteredItems = result;
      } else {
        this.filteredItems = this.items;
      }
    },

    choose(i) {
      this.backgroundImage = this.items[i].pic;
      this.show = true;
      console.log(this.items[i].pic);
    },

    left() {
      for(let i = 0; i<= this.items; i++){
        this.counter--;
        if(this.counter < 0){
        this.backgroundImage = this.items[0].pic;
          }
      }
        console.log("i was clicked");
        console.log(this.items[0].pic);
    },
    right(r) {
      this.counter++;
      if (this.counter >= this.items[r].pic.length) {
        this.counter = 0;
        this.backgroundImage = this.items[r].pic;
      }
    },
    close() {
      this.show = false;
    }
  },

  mounted() {
    this.filteredItems = this.items;
  }
};
</script>

<style scoped>
.lightbox-container {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 999;
  background: rgba(0, 0, 0, 0.6) !important;
  /* display: none; */
}
/* .show {
  display: block;
} */

.lightbox-holder {
  position: relative;
}
.lightbox-item {
  min-height: 80vh;
  background: center/cover fixed no-repeat;
  border-radius: 0.3rem;
}
.lightbox-close {
  color: var(--mainPink);
  font-size: 3rem;
  transition: all 1s ease-in-out;
  cursor: pointer;
}
.lightbox-close:hover {
  color: var(--mainYellow);
}

.lightbox-control {
  position: absolute;
  font-size: 4rem;
  color: var(--mainPink);
  transition: all 1s linear;
  cursor: pointer;
}
.lightbox-control:hover {
  color: var(--mainYellow);
}
.btnLeft {
  top: 50%;
  left: 0;
  transform: translateX(-60%);
}
.btnRight {
  top: 50%;
  right: 0;
  transform: translateX(60%);
}
</style>

