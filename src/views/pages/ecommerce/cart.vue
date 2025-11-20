<script>
import Layout from "../../layouts/main";
import PageHeader from "@/components/page-header";
import appConfig from "@/app.config";

/**
 * Cart component
 */
export default {
  page: {
    title: "Cart",
    meta: [
      {
        name: "description",
        content: appConfig.description,
      },
    ],
  },
  components: {
    Layout,
    PageHeader,
  },
  data() {
    return {
      title: "Cart",
      quantityNike: 2,
      quantityAdidas: 1,
      items: [
        {
          text: "Ecommerce",
        },
        {
          text: "Cart",
          active: true,
        },
      ],
    };
  },
  methods: {
    incrementNike() {
      this.quantityNike++;
    },
    decrementNike() {
      if (this.quantityNike > 1) {
        this.quantityNike--;
      }
    },
    incrementAdidas() {
      this.quantityAdidas++;
    },
    decrementAdidas() {
      if (this.quantityAdidas > 1) {
        this.quantityAdidas--;
      }
    },
  },
  middleware: "authentication",
};
</script>

<template>
  <Layout>
    <PageHeader :title="title" :items="items" />
    <BRow>
      <BCol cols="xl-8">
        <BCard no-body class="border shadow-none">
          <BCardBody>
            <div class="d-flex align-items-start border-bottom pb-3">
              <div class="flex-shrink-0 me-4">
                <img src="@/assets/images/product/img-1.png" alt="" class="avatar-lg">
              </div>
              <div class="flex-grow-1 align-self-center overflow-hidden">
                <div>
                  <h5 class="text-truncate font-size-16">
                    <router-link to="/ecommerce/product-detail/1" class="text-reset ">Nike
                      N012 Running Shoes
                    </router-link>
                  </h5>
                  <p class="mb-1">Color : <span class="fw-medium">Gray</span></p>
                  <p>Size : <span class="fw-medium">08</span></p>
                </div>
              </div>
              <div class="ms-2">
                <ul class="list-inline mb-0 font-size-16">
                  <li class="list-inline-item">
                    <BLink href="#" class="text-muted px-2">
                      <i class="uil uil-trash-alt"></i>
                    </BLink>
                  </li>
                  <li class="list-inline-item">
                    <BLink href="#" class="text-muted px-2">
                      <i class="uil uil-heart"></i>
                    </BLink>
                  </li>
                </ul>
              </div>
            </div>
            <div>
              <BRow>
                <BCol md="4">
                  <div class="mt-3">
                    <p class="text-muted mb-2">Price</p>
                    <h5 class="font-size-16">$260</h5>
                  </div>
                </BCol>
                <BCol md="4">
                  <div class="mt-3">
                    <p class="text-muted mb-2">Quantity</p>
                    <div style="width: 120px;" class="product-cart-touchspin">
                      <div class="input-group bootstrap-touchspin bootstrap-touchspin-injected">
                        <span class="input-group-btn input-group-prepend">
                          <button class="btn btn-primary bootstrap-touchspin-down" type="button"
                            @click="decrementNike">−</button>
                        </span>
                        <input data-toggle="touchspin" type="text" v-model="quantityNike" class="form-control">
                        <span class="input-group-btn input-group-append">
                          <button class="btn btn-primary bootstrap-touchspin-up" type="button"
                            @click="incrementNike">+</button>
                        </span>
                      </div>
                    </div>
                  </div>
                </BCol>
                <BCol md="4">
                  <div class="mt-3">
                    <p class="text-muted mb-2">Total</p>
                    <h5 class="font-size-16">${{ 260 * quantityNike }}</h5>
                  </div>
                </BCol>
              </BRow>
            </div>
          </BCardBody>
        </BCard>

        <BCard no-body class="border shadow-none">
          <BCardBody>
            <div class="d-flex align-items-start border-bottom pb-3">
              <div class="flex-shrink-0 me-4">
                <img src="@/assets/images/product/img-2.png" alt="" class="avatar-lg">
              </div>
              <div class="flex-grow-1 align-self-center overflow-hidden">
                <div>
                  <h5 class="text-truncate font-size-16">
                    <router-link to="/ecommerce/product-detail/2" class="text-reset ">Adidas Running Shoes</router-link>
                  </h5>
                  <p class="mb-1">Color : <span class="fw-medium">Black</span></p>
                  <p>Size : <span class="fw-medium">09</span></p>
                </div>
              </div>
              <div class="ms-2">
                <ul class="list-inline mb-0 font-size-16">
                  <li class="list-inline-item" data-bs-toggle="tooltip" data-placement="top" aria-label="Remove"
                    data-bs-original-title="Remove">
                    <a href="#" class="text-muted px-2">
                      <i class="uil uil-trash-alt"></i>
                    </a>
                  </li>
                  <li class="list-inline-item" data-bs-toggle="tooltip" data-placement="top" aria-label="Add Wishlist"
                    data-bs-original-title="Add Wishlist">
                    <a href="#" class="text-muted px-2">
                      <i class="uil uil-heart"></i>
                    </a>
                  </li>
                </ul>
              </div>
            </div>
            <div>
              <BRow>
                <BCol md="4">
                  <div class="mt-3">
                    <p class="text-muted mb-2">Price</p>
                    <h5 class="font-size-16">$260</h5>
                  </div>
                </BCol>
                <BCol md="4">
                  <div class="mt-3">
                    <p class="text-muted mb-2">Quantity</p>
                    <div style="width: 120px;" class="product-cart-touchspin">
                      <div class="input-group bootstrap-touchspin bootstrap-touchspin-injected">
                        <span class="input-group-btn input-group-prepend">
                          <button class="btn btn-primary bootstrap-touchspin-down" type="button"
                            @click="decrementAdidas">−</button>
                        </span>
                        <input data-toggle="touchspin" type="text" v-model="quantityAdidas" class="form-control">
                        <span class="input-group-btn input-group-append">
                          <button class="btn btn-primary bootstrap-touchspin-up" type="button"
                            @click="incrementAdidas">+</button>
                        </span>
                      </div>
                    </div>
                  </div>
                </BCol>
                <BCol md="4">
                  <div class="mt-3">
                    <p class="text-muted mb-2">Total</p>
                    <h5 class="font-size-16">${{ 260 * quantityAdidas }}</h5>
                  </div>
                </BCol>
              </BRow>
            </div>
          </BCardBody>
        </BCard>

        <BRow rows="mt-4">
          <BCol sm="6">
            <router-link to="/ecommerce/products" class="btn btn-link text-muted">
              <i class="uil uil-arrow-left me-1"></i> Continue Shopping
            </router-link>
          </BCol>

          <BCol sm="6">
            <div class="text-sm-end mt-2 mt-sm-0">
              <router-link to="/ecommerce/checkout" class="btn btn-success">
                <i class="uil uil-shopping-cart-alt me-1"></i> Checkout
              </router-link>
            </div>
          </BCol>
        </BRow>
      </BCol>

      <BCol cols="xl-4">
        <div class="mt-5 mt-lg-0">
          <div class="card border shadow-none">
            <div class="card-header bg-transparent border-bottom py-3 px-4">
              <h5 class="font-size-16 mb-0">
                Order Summary
                <span class="float-end">#MN0124</span>
              </h5>
            </div>
            <BCardBody class="p-4">
              <div class="table-responsive">
                <BTableSimple class="mb-0">
                  <BTbody>
                    <BTr>
                      <BTd>Sub Total :</BTd>
                      <BTd class="text-end">$ {{ 260 * (quantityNike + quantityAdidas) }}</BTd>
                    </BTr>
                    <BTr>
                      <BTd>Discount :</BTd>
                      <BTd class="text-end">- $ {{ (260 * (quantityNike + quantityAdidas)) / 10 }}</BTd>
                    </BTr>
                    <BTr>
                      <BTd>Shipping Charge :</BTd>
                      <BTd class="text-end">$ 25</BTd>
                    </BTr>
                    <BTr>
                      <BTd>Estimated Tax :</BTd>
                      <BTd class="text-end">$ {{ (260 * (quantityNike + quantityAdidas) * 0.0234).toFixed(2) }}</BTd>
                    </BTr>
                    <BTr class="bg-light">
                      <BTh>Total :</BTh>
                      <BTd class="text-end">
                        <span class="fw-bold">$ {{ ((260 * (quantityNike + quantityAdidas)) - ((260 * (quantityNike +
                          quantityAdidas)) / 10) + 25 + (260 * (quantityNike + quantityAdidas) * 0.0234)).toFixed(2)
                        }}</span>
                      </BTd>
                    </BTr>
                  </BTbody>
                </BTableSimple>
              </div>
            </BCardBody>
          </div>
        </div>
      </BCol>
    </BRow>
  </Layout>
</template>
