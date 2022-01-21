<template>
  <div id="products">
    <div class="item" v-for="item of products" :key="item.id">
      <div class="description">
        <img :src="item.img" alt="" />
        <div class="details">
          <div class="top">
            <h2>{{ item.name }}</h2>
            <span>{{ item.color }}</span>
          </div>
          <div class="bottom">
            <p>{{ "$" + item.price }}</p>
          </div>
        </div>
      </div>
      <div class="options">
        <div class="color_options">
          <button
            @click="ChangeColor(item, colors)"
            v-for="item of colors"
            :key="item.id"
            :class="{ active: item.isActive }"
            class="choice"
          >
            {{ item.colour }}
          </button>
        </div>
        <div v-for="key of specs" :key="key.id" class="memory">
          <div
            @click="Sort_out(key, specs)"
            :class="{ active1: key.active }"
            class="option"
          >
            <p>{{ `${key.memory} GB SSD` }}</p>
            <p>{{key.add_p == 0 ? "" : `+$${key.add_p}` }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isWhite: false,
      isGrey: false,
      colors: [
        {
          id: 1,
          colour: "White",
          img: "images/Macbook_1.png",
          isActive: true,
        },
        {
          id: 2,
          colour: "Space Gray",
          img: "images/Macbook_2.png",
          isActive: false,
        },
      ],
      specs: [
        {
          specs_id: 1,
          cost: 1999,
          add_p: 0,
          memory: 512,
          active: true,
        },
        {
          specs_id: 2,
          cost: 1999,
          add_p: 200,
          memory: 1,
          active: false,
        },
        {
          specs_id: 3,
          cost: 1999,
          add_p: 600,
          memory: 2,
          active: false,
        },
        {
          specs_id: 4,
          cost: 1999,
          add_p: 1200,
          memory: 4,
          active: false,
        },
      ],
      products: [
        {
          name: "Macbook Pro",
          color: "White",
          img: "images/Macbook_1.png",
          memory: 512,
          price: 1999,
          color_id: 1,
          specs: 1,
        },
      ],
    };
  },
  methods: {
    ChangeColor: function (par, colors) {
      let sort = this.colors.filter((item) => item.colour == par.colour)[0];
      for (let item of this.products) {
        item.color = sort.colour;
        item.img = sort.img;
      }
      for (let item of colors) {
        item.isActive = false;
        par.isActive = true;
      }
    },
    Sort_out: function (num, specs) {
      let sort = this.specs.filter((item) => item.add_p == num.add_p)[0];
      for (let item of this.products) {
        item.price = sort.add_p + sort.cost;
      }
        
      for (let item of specs) {
        item.active = false;
        num.active = true;
      }
      console.log(num)
      console.log(specs)
    },
  },
};
</script>

<style>
.products {
  margin: 0 auto;
  font-family: Gilroy;
}
.description {
  display: flex;
  justify-content: center;
  align-items: center;
  grid-gap: 24px;
}
.top {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.top h2 {
  font-size: 32px;
}
.top span {
  font-weight: 700;
  color: #0071e3;
}
.bottom {
  display: flex;
  align-items: flex-start;
}

.bottom p {
  font-size: 32px;
  font-weight: 700;
}
.color_options {
  display: flex;
  justify-content: center;
  grid-gap: 15px;
}
.choice {
  font-family: "Gilroy";
  width: 155px;
  height: 42px;
  background-color: #cfe7ff;
  border-radius: 10px;
  color: #fff;
  border: none;
  font-weight: 600;
}
.active {
  background-color: #0071e3;
  color: #fff;
}
.options {
  font-family: Gilroy;
  margin: 20px;
}
.memory {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-weight: 700;
}
.memory div {
  width: 300px;
  height: 57px;
  border-radius: 10px;
  margin-top: 10px;
  border: 2px solid #cfe7ff;
}
.memory .option {
  display: flex;
  justify-content: space-between;
  padding: 0 10px;
}
.active1 {
  border: 2px solid #0071e3 !important;
}
</style>
