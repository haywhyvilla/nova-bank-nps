<script>
import Layout from "../../layouts/main";
import PageHeader from "@/components/page-header";
import appConfig from "@/app.config";
import Slider from "@vueform/slider";

import { productData } from "./data-products";
/**
 * Products component
 */
export default {
  components: { Layout, PageHeader, Slider },
  page: {
    title: "Products",
    meta: [
      {
        name: "description",
        content: appConfig.description,
      },
    ],
  },
  data() {
    return {
      productData: productData,
      title: "Products",
      items: [
        {
          text: "Ecommerce",
        },
        {
          text: "Products",
          active: true,
        },
      ],
      sliderPrice: 800,
      currentPage: 1,
    };
  },
  middleware: "authentication",
  methods: {
    valuechange(value) {
      this.productData = productData.filter(function (product) {
        return product.newprice <= value.currentValue;
      });
    },
  },
};
</script>

<template>
  <Layout>
    <PageHeader :title="title" :items="items" />
    <BRow>
      <BCol lg="4" class="col-xl-3">
        <BCard no-body>
          <div class="card-header bg-transparent border-bottom">
            <h5 class="mb-0">Filters</h5>
          </div>

          <div class="p-4">
            <h5 class="font-size-14 mb-3">Categories</h5>
            <div class="custom-accordion">
              <a class="text-body fw-semibold pb-2 d-block" data-toggle="collapse" href="javascript: void(0);" role="button" aria-expanded="false" v-b-toggle.categories-collapse>
                <i class="mdi mdi-chevron-up accor-down-icon text-primary me-1"></i>
                Footwear
              </a>
              <BCollapse visible id="categories-collapse">
                <div class="card p-2 border shadow-none">
                  <ul class="list-unstyled categories-list mb-0">
                    <li>
                      <BLink href="#">
                        <i class="mdi mdi-circle-medium me-1"></i> Formal Shoes
                      </BLink>
                    </li>
                    <li class="active">
                      <BLink href="#">
                        <i class="mdi mdi-circle-medium me-1"></i> Sports Shoes
                      </BLink>
                    </li>
                    <li>
                      <BLink href="#">
                        <i class="mdi mdi-circle-medium me-1"></i> casual Shoes
                      </BLink>
                    </li>
                    <li>
                      <BLink href="#">
                        <i class="mdi mdi-circle-medium me-1"></i> Sandals
                      </BLink>
                    </li>
                    <li>
                      <BLink href="#">
                        <i class="mdi mdi-circle-medium me-1"></i> Slippers
                      </BLink>
                    </li>
                  </ul>
                </div>
              </BCollapse>
            </div>
          </div>

          <div class="p-4 border-top">
            <div>
              <h5 class="font-size-14 mb-4">Price</h5>
              <Slider v-model="sliderPrice" :min="0" :max="1000" @dragEnd="valuechange" />
            </div>
          </div>

          <div class="custom-accordion">
            <div class="p-4 border-top">
              <div>
                <h5 class="font-size-14 mb-0">
                  <BLink href="javascript: void(0);" class="text-dark d-block" data-toggle="collapse" v-b-toggle.filtersizes-collapse>
                    Sizes
                    <i class="mdi mdi-chevron-up float-end accor-down-icon"></i>
                  </BLink>
                </h5>

                <BCollapse visible id="filtersizes-collapse">
                  <div class="mt-4">
                    <div class="media align-items-center">
                      <div class="media-body">
                        <h5 class="font-size-15 mb-0">Select Sizes</h5>
                      </div>
                      <div class="w-xs">
                        <select class="form-select">
                          <option value="1">3</option>
                          <option value="2">4</option>
                          <option value="3">5</option>
                          <option value="4">6</option>
                          <option value="5" selected="">7</option>
                          <option value="6">8</option>
                          <option value="7">9</option>
                          <option value="8">10</option>
                        </select>
                      </div>
                    </div>
                  </div>
                </BCollapse>
              </div>
            </div>

            <div class="p-4 border-top">
              <div>
                <h5 class="font-size-14 mb-0">
                  <BLink href="javascript: void(0);" class="text-dark d-block" data-toggle="collapse" v-b-toggle.filterprodductcolor-collapse>
                    Colors
                    <i class="mdi mdi-chevron-up float-end accor-down-icon"></i>
                  </BLink>
                </h5>

                <BCollapse visible id="filterprodductcolor-collapse">
                  <div class="mt-4">
                    <div class="custom-control custom-checkbox mt-2">
                      <input type="checkbox" class="custom-control-input" id="productcolorCheck1" />
                      <label class="custom-control-label" for="productcolorCheck1">
                        <i class="mdi mdi-circle text-dark mx-1"></i>
                        Black
                      </label>
                    </div>
                    <div class="custom-control custom-checkbox mt-2">
                      <input type="checkbox" class="custom-control-input" id="productcolorCheck2" />
                      <label class="custom-control-label" for="productcolorCheck2">
                        <i class="mdi mdi-circle text-light mx-1"></i>
                        White
                      </label>
                    </div>
                    <div class="custom-control custom-checkbox mt-2">
                      <input type="checkbox" class="custom-control-input" id="productcolorCheck3" />
                      <label class="custom-control-label" for="productcolorCheck3">
                        <i class="mdi mdi-circle text-secondary mx-1"></i>
                        Gray
                      </label>
                    </div>
                    <div class="custom-control custom-checkbox mt-2">
                      <input type="checkbox" class="custom-control-input" id="productcolorCheck4" />
                      <label class="custom-control-label" for="productcolorCheck4">
                        <i class="mdi mdi-circle text-primary mx-1"></i>
                        Blue
                      </label>
                    </div>
                    <div class="custom-control custom-checkbox mt-2">
                      <input type="checkbox" class="custom-control-input" id="productcolorCheck5" />
                      <label class="custom-control-label" for="productcolorCheck5">
                        <i class="mdi mdi-circle text-success mx-1"></i>
                        green
                      </label>
                    </div>
                    <div class="custom-control custom-checkbox mt-2">
                      <input type="checkbox" class="custom-control-input" id="productcolorCheck6" />
                      <label class="custom-control-label" for="productcolorCheck6">
                        <i class="mdi mdi-circle text-danger mx-1"></i>
                        Red
                      </label>
                    </div>
                    <div class="custom-control custom-checkbox mt-2">
                      <input type="checkbox" class="custom-control-input" id="productcolorCheck7" />
                      <label class="custom-control-label" for="productcolorCheck7">
                        <i class="mdi mdi-circle text-warning mx-1"></i>
                        Yellow
                      </label>
                    </div>
                    <div class="custom-control custom-checkbox mt-2">
                      <input type="checkbox" class="custom-control-input" id="productcolorCheck8" />
                      <label class="custom-control-label" for="productcolorCheck8">
                        <i class="mdi mdi-circle text-purple mx-1"></i>
                        Purple
                      </label>
                    </div>
                  </div>
                </BCollapse>
              </div>
            </div>

            <div class="p-4 border-top">
              <div>
                <h5 class="font-size-14 mb-0">
                  <BLink href="javascript: void(0);" class="text-dark d-block" data-toggle="collapse" v-b-toggle.filterproduct-color-collapse>
                    Customer Rating
                    <i class="mdi mdi-chevron-up float-end accor-down-icon"></i>
                  </BLink>
                </h5>

                <BCollapse visible id="filterproduct-color-collapse">
                  <div class="mt-4">
                    <div class="custom-control custom-radio mt-2">
                      <input type="radio" id="productratingRadio1" name="productratingRadio1" class="custom-control-input" />
                      <label class="custom-control-label" for="productratingRadio1">
                        4
                        <i class="mdi mdi-star text-warning"></i> & Above
                      </label>
                    </div>
                    <div class="custom-control custom-radio mt-2">
                      <input type="radio" id="productratingRadio2" name="productratingRadio1" class="custom-control-input" />
                      <label class="custom-control-label" for="productratingRadio2">
                        3
                        <i class="mdi mdi-star text-warning"></i> & Above
                      </label>
                    </div>
                    <div class="custom-control custom-radio mt-2">
                      <input type="radio" id="productratingRadio3" name="productratingRadio1" class="custom-control-input" />
                      <label class="custom-control-label" for="productratingRadio3">
                        2
                        <i class="mdi mdi-star text-warning"></i> & Above
                      </label>
                    </div>
                    <div class="custom-control custom-radio mt-2">
                      <input type="radio" id="productratingRadio4" name="productratingRadio1" class="custom-control-input" />
                      <label class="custom-control-label" for="productratingRadio4">
                        1
                        <i class="mdi mdi-star text-warning"></i>
                      </label>
                    </div>
                  </div>
                </BCollapse>
              </div>
            </div>

            <div class="p-4 border-top">
              <div>
                <h5 class="font-size-14 mb-0">
                  <BLink href="#filterproduct-discount-collapse" class="text-dark d-block" data-toggle="collapse" v-b-toggle.filterproduct-discount-collapse>
                    Discount
                    <i class="mdi mdi-chevron-up float-end accor-down-icon"></i>
                  </BLink>
                </h5>

                <BCollapse id="filterproduct-discount-collapse">
                  <div class="mt-4">
                    <div class="custom-control custom-radio mt-2">
                      <input type="radio" id="productdiscountRadio1" name="productdiscountRadio" class="custom-control-input" />
                      <label class="custom-control-label" for="productdiscountRadio1">50% or more</label>
                    </div>
                    <div class="custom-control custom-radio mt-2">
                      <input type="radio" id="productdiscountRadio2" name="productdiscountRadio" class="custom-control-input" />
                      <label class="custom-control-label" for="productdiscountRadio2">40% or more</label>
                    </div>
                    <div class="custom-control custom-radio mt-2">
                      <input type="radio" id="productdiscountRadio3" name="productdiscountRadio" class="custom-control-input" />
                      <label class="custom-control-label" for="productdiscountRadio3">30% or more</label>
                    </div>
                    <div class="custom-control custom-radio mt-2">
                      <input type="radio" id="productdiscountRadio4" name="productdiscountRadio" class="custom-control-input" />
                      <label class="custom-control-label" for="productdiscountRadio4">20% or more</label>
                    </div>
                    <div class="custom-control custom-radio mt-2">
                      <input type="radio" id="productdiscountRadio5" name="productdiscountRadio" class="custom-control-input" />
                      <label class="custom-control-label" for="productdiscountRadio5">10% or more</label>
                    </div>
                    <div class="custom-control custom-radio mt-2">
                      <input type="radio" id="productdiscountRadio6" name="productdiscountRadio" class="custom-control-input" />
                      <label class="custom-control-label" for="productdiscountRadio6">Less than 10%</label>
                    </div>
                  </div>
                </BCollapse>
              </div>
            </div>
          </div>
        </BCard>
      </BCol>

      <BCol lg="8" class="col-xl-9">
        <BCard no-body>
          <BCardBody>
            <div>
              <BRow>
                <BCol md="6">
                  <div>
                    <h5>Showing result for "Shoes"</h5>
                    <ol class="breadcrumb p-0 bg-transparent mb-2">
                      <li class="breadcrumb-item">
                        <BLink href="javascript: void(0);">Footwear</BLink>
                      </li>
                      <li class="breadcrumb-item active">Shoes</li>
                    </ol>
                  </div>
                </BCol>

                <BCol md="6">
                  <div class="form-inline float-md-end">
                    <div class="search-box ms-2">
                      <div class="position-relative">
                        <input type="text" class="form-control bg-light border-light rounded" placeholder="Search..." />
                        <i class="mdi mdi-magnify search-icon"></i>
                      </div>
                    </div>
                  </div>
                </BCol>
              </BRow>

              <ul class="nav nav-tabs nav-tabs-custom mt-3 mb-2 ecommerce-sortby-list">
                <li class="nav-item">
                  <BLink class="nav-link disabled fw-medium" href="#" tabindex="-1" aria-disabled="true">Sort by:</BLink>
                </li>
                <li class="nav-item">
                  <BLink class="nav-link active" href="#">Popularity</BLink>
                </li>
                <li class="nav-item">
                  <BLink class="nav-link" href="#">Newest</BLink>
                </li>
                <li class="nav-item">
                  <BLink class="nav-link" href="#">Discount</BLink>
                </li>
              </ul>

              <BRow>
                <BCol class="col-xl-4 col-sm-6" v-for="(item, index) in productData" :key="index">
                  <div class="product-box">
                    <div class="product-img pt-4 px-4">
                      <div class="product-ribbon badge badge-danger">
                        - {{ item.discount }} %
                      </div>
                      <div class="product-wishlist">
                        <BLink href="#">
                          <i class="mdi mdi-heart-outline"></i>
                        </BLink>
                      </div>
                      <img :src="item.image" alt class="img-fluid mx-auto d-block" />
                    </div>

                    <div class="text-center product-content p-4">
                      <h5 class="mb-1">
                        <router-link :to="'/ecommerce/product-detail/' + item.id" class="text-dark">{{ item.name
                        }}</router-link>
                      </h5>
                      <p class="text-muted font-size-13">{{ item.disc }}</p>

                      <h5 class="mt-3 mb-0">
                        <span class="text-muted me-2">
                          <del>${{ item.oldprice }}</del>
                        </span>
                        ${{ item.newprice }}
                      </h5>

                      <ul class="list-inline mb-0 text-muted product-color">
                        <li class="list-inline-item">Colors :</li>
                        <li class="list-inline-item" v-for="(item, index) in item.colors" :key="index">
                          <i :class="`mdi mdi-circle text-${item}`"></i>
                        </li>
                      </ul>
                    </div>
                  </div>
                </BCol>
              </BRow>

              <BRow class="mt-4">
                <BCol lg="12">
                  <BPagination v-if="productData.length > 0" class="justify-content-center" pills v-model="currentPage" :total-rows="productData.length" :per-page="6" aria-controls="my-table"></BPagination>
                </BCol>
              </BRow>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>
  </Layout>
</template>
<!-- 
<style>
@import "@vueform/slider/themes/default.css";
</style> -->
