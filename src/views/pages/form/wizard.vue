<script>
import Layout from "../../layouts/main";
import PageHeader from "@/components/page-header";
import appConfig from "@/app.config";

/**
 * Form wizard component
 */
export default {
  page: {
    title: "Form Wizard",
    meta: [
      {
        name: "description",
        content: appConfig.description,
      },
    ],
  },
  components: {
    PageHeader,
    Layout,
  },
  data() {
    return {
      activeTab: 0,
      activeVerTab: 0,
      title: "Form Wizard",
      items: [
        {
          text: "Forms",
          href: "/",
        },
        {
          text: "Form Wizard",
          active: true,
        },
      ],
    };
  },
  methods: {
    setActiveTab(index) {
      this.activeTab = index;
    },
    setActiveVerTab(index) {
      this.activeVerTab = index;
    },
  },
  middleware: "authentication",
};
</script>

<template>
  <Layout>
    <PageHeader :title="title" :items="items" />
    <BRow>
      <BCol lg="12">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Basic Wizard</BCardTitle>
            <div id="basic-example" class="wizard clearfix">
              <div class="steps clearfix">
                <ul>
                  <li :class="{ current: activeTab === 0, done: activeTab > 0 }">
                    <BLink id="basic-example-t-0" href="#" @click="setActiveTab(0)">
                      <span class="number">1.</span> Seller Details
                    </BLink>
                  </li>
                  <li :class="{ current: activeTab === 1, done: activeTab > 1 }">
                    <BLink id="basic-example-t-1" href="#" @click="setActiveTab(1)">
                      <span class="number">2.</span> Company Document
                    </BLink>
                  </li>
                  <li :class="{ current: activeTab === 2, done: activeTab > 2 }">
                    <BLink id="basic-example-t-2" href="#" @click="setActiveTab(2)">
                      <span class="number">3.</span> Bank Details
                    </BLink>
                  </li>
                  <li :class="{ current: activeTab === 3, done: activeTab > 3 }">
                    <BLink id="basic-example-t-3" href="#" @click="setActiveTab(3)">
                      <span class="number">4.</span> Confirm Detail
                    </BLink>
                  </li>
                </ul>
              </div>
              <div class="content clearfix">
                <!-- Seller Details -->
                <h3 id="basic-example-h-0" class="title" :class="{ 'current': activeTab === 0 }">Seller Details</h3>
                <section id="basic-example-p-0" class="body"
                  :class="{ 'd-block current': activeTab === 0, 'd-none': activeTab !== 0 }">
                  <form>
                    <BRow>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="basicpill-firstname-input">First Name</label>
                          <input type="text" class="form-control" id="basicpill-firstname-input"
                            placeholder="Enter your First name">
                        </div>
                      </BCol>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="basicpill-lastname-input">Last Name</label>
                          <input type="text" class="form-control" id="basicpill-lastname-input"
                            placeholder="Enter your Last Name">
                        </div>
                      </BCol>
                    </BRow>
                    <BRow>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="basicpill-phoneno-input">Phone</label>
                          <input type="text" class="form-control" id="basicpill-phoneno-input"
                            placeholder="Enter your Phone Number">
                        </div>
                      </BCol>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="basicpill-email-input">Email</label>
                          <input type="email" class="form-control" id="basicpill-email-input"
                            placeholder="Enter your email address">
                        </div>
                      </BCol>
                    </BRow>
                    <BRow>
                      <BCol lg="12">
                        <div class="mb-3">
                          <label for="basicpill-address-input">Address</label>
                          <textarea id="basicpill-address-input" class="form-control" rows="2"
                            placeholder="Enter your Address"></textarea>
                        </div>
                      </BCol>
                    </BRow>
                  </form>
                </section>

                <!-- Company Document -->
                <h3 id="basic-example-h-1" class="title" :class="{ 'current': activeTab === 1 }">Company Document</h3>
                <section id="basic-example-p-1" class="body"
                  :class="{ 'd-block current': activeTab === 1, 'd-none': activeTab !== 1 }">
                  <form>
                    <BRow>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="basicpill-pancard-input">PAN Card</label>
                          <input type="text" class="form-control" id="basicpill-pancard-input"
                            placeholder="Enter your Pancard Number">
                        </div>
                      </BCol>

                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="basicpill-vatno-input">VAT/TIN No.</label>
                          <input type="text" class="form-control" id="basicpill-vatno-input"
                            placeholder="Enter your VAT/TIN number.">
                        </div>
                      </BCol>
                    </BRow>
                    <BRow>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="basicpill-cstno-input">CST No.</label>
                          <input type="text" class="form-control" id="basicpill-cstno-input"
                            placeholder="Enter your CST number">
                        </div>
                      </BCol>

                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="basicpill-servicetax-input">Service Tax No.</label>
                          <input type="text" class="form-control" id="basicpill-servicetax-input"
                            placeholder="Enter your Service Tax number">
                        </div>
                      </BCol>
                    </BRow>
                    <BRow>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="basicpill-companyuin-input">Company UIN</label>
                          <input type="text" class="form-control" id="basicpill-companyuin-input"
                            placeholder="Enter your Company UIN number">
                        </div>
                      </BCol>

                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="basicpill-declaration-input">Declaration</label>
                          <input type="text" class="form-control" id="basicpill-Declaration-input"
                            placeholder="Enter your Declaration">
                        </div>
                      </BCol>
                    </BRow>
                  </form>
                </section>

                <!-- Bank Details -->
                <h3 id="basic-example-h-2" class="title" :class="{ 'current': activeTab === 2 }">Bank Details</h3>
                <section id="basic-example-p-2" class="body"
                  :class="{ 'd-block current': activeTab === 2, 'd-none': activeTab !== 2 }">
                  <div>
                    <form>
                      <BRow>
                        <BCol lg="6">
                          <div class="mb-3">
                            <label for="basicpill-namecard-input">Name on Card</label>
                            <input type="text" class="form-control" id="basicpill-namecard-input"
                              placeholder="Enter your Name on Card">
                          </div>
                        </BCol>

                        <BCol lg="6">
                          <div class="mb-3">
                            <label>Credit Card Type</label>
                            <select class="form-select">
                              <option selected="">Select Card Type</option>
                              <option value="AE">American Express</option>
                              <option value="VI">Visa</option>
                              <option value="MC">MasterCard</option>
                              <option value="DI">Discover</option>
                            </select>
                          </div>
                        </BCol>
                      </BRow>
                      <BRow>
                        <BCol lg="6">
                          <div class="mb-3">
                            <label for="basicpill-cardno-input">Credit Card Number</label>
                            <input type="text" class="form-control" id="basicpill-cardno-input"
                              placeholder="Enter your Enter your Credit Card Number">
                          </div>
                        </BCol>

                        <BCol lg="6">
                          <div class="mb-3">
                            <label for="basicpill-card-verification-input">Card Verification Number</label>
                            <input type="text" class="form-control" id="basicpill-card-verification-input"
                              placeholder="Enter your Card Verification Number">
                          </div>
                        </BCol>
                      </BRow>
                      <BRow>
                        <BCol lg="6">
                          <div class="mb-3">
                            <label for="basicpill-expiration-input">Expiration Date</label>
                            <input type="text" class="form-control" id="basicpill-expiration-input"
                              placeholder="Enter your Expiration Date">
                          </div>
                        </BCol>

                      </BRow>
                    </form>
                  </div>
                </section>

                <!-- Confirm Details -->
                <h3 id="basic-example-h-3" class="title" :class="{ 'current': activeTab === 3 }">Confirm Detail</h3>
                <section id="basic-example-p-3" class="body"
                  :class="{ 'd-block current': activeTab === 3, 'd-none': activeTab !== 3 }">
                  <BRow class="justify-content-center">
                    <BCol lg="6">
                      <div class="text-center">
                        <div class="mb-4">
                          <i class="mdi mdi-check-circle-outline text-success display-4"></i>
                        </div>
                        <div>
                          <h5>Confirm Detail</h5>
                          <p class="text-muted">If several languages coalesce, the grammar of the resulting</p>
                        </div>
                      </div>
                    </BCol>
                  </BRow>
                </section>
              </div>

              <div class="actions clearfix">
                <ul>
                  <li class="disabled" v-if="activeTab === 0">
                    <BLink href="#">Previous</BLink>
                  </li>
                  <li @click="setActiveTab(activeTab - 1)" v-if="activeTab > 0">
                    <BLink href="#">Previous</BLink>
                  </li>
                  <li @click="setActiveTab(activeTab + 1)" v-if="activeTab < 3">
                    <BLink href="#">Next</BLink>
                  </li>
                  <li v-if="activeTab === 3">
                    <BLink href="#">Finish</BLink>
                  </li>
                </ul>
              </div>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
      <BCol lg="12">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Tab Wizard</BCardTitle>

            <div id="vertical-example" class="vertical-wizard wizard clearfix vertical">
              <div class="steps clearfix">
                <ul>
                  <li :class="{ current: activeVerTab === 0, done: activeVerTab > 0 }">
                    <BLink id="vertical-example-t-0" href="#" @click="setActiveVerTab(0)">
                      <span class="number">1.</span> Seller Details
                    </BLink>
                  </li>
                  <li :class="{ current: activeVerTab === 1, done: activeVerTab > 1 }">
                    <BLink id="vertical-example-t-1" href="#" @click="setActiveVerTab(1)">
                      <span class="number">2.</span> Company Document
                    </BLink>
                  </li>
                  <li :class="{ current: activeVerTab === 2, done: activeVerTab > 2 }">
                    <BLink id="vertical-example-t-2" href="#" @click="setActiveVerTab(2)">
                      <span class="number">3.</span> Bank Details
                    </BLink>
                  </li>
                  <li :class="{ current: activeVerTab === 3, done: activeVerTab > 3 }">
                    <BLink id="vertical-example-t-3" href="#" @click="setActiveVerTab(3)">
                      <span class="number">4.</span> Confirm Detail
                    </BLink>
                  </li>
                </ul>
              </div>
              <div class="content clearfix">
                <!-- Seller Details -->
                <h3 id="vertical-example-h-0" class="title" :class="{ 'current': activeVerTab === 0 }"> Seller Details
                </h3>
                <section id="vertical-example-p-0"
                  :class="{ 'd-block current': activeVerTab === 0, 'd-none': activeVerTab !== 0 }">
                  <form>
                    <BRow>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="verticalnav-firstname-input">First Name</label>
                          <input type="text" class="form-control" id="verticalnav-firstname-input"
                            placeholder="Enter your First Name">
                        </div>
                      </BCol>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="verticalnav-lastname-input">Last name</label>
                          <input type="text" class="form-control" id="verticalnav-lastname-input"
                            placeholder="Enter your Last Name">
                        </div>
                      </BCol>
                    </BRow>
                    <BRow>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="verticalnav-phoneno-input">Phone</label>
                          <input type="text" class="form-control" id="verticalnav-phoneno-input"
                            placeholder="Enter your Phone">
                        </div>
                      </BCol>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="verticalnav-email-input">Email</label>
                          <input type="email" class="form-control" id="verticalnav-email-input"
                            placeholder="Enter your Email address">
                        </div>
                      </BCol>
                    </BRow>
                    <BRow>
                      <BCol lg="12">
                        <div class="mb-3">
                          <label for="verticalnav-address-input">Address</label>
                          <textarea id="verticalnav-address-input" class="form-control" rows="2"
                            placeholder="Enter your Address"></textarea>
                        </div>
                      </BCol>
                    </BRow>
                  </form>
                </section>

                <!-- Company Document -->
                <h3 id="vertical-example-h-1" class="title" :class="{ 'current': activeVerTab === 0 }"> Company Document
                </h3>
                <section id="vertical-example-p-1"
                  :class="{ 'd-block current': activeVerTab === 1, 'd-none': activeVerTab !== 1 }">
                  <form>
                    <BRow>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="verticalnav-pancard-input">PAN Card</label>
                          <input type="text" class="form-control" id="verticalnav-pancard-input"
                            placeholder="Enter your PAN Card number">
                        </div>
                      </BCol>

                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="verticalnav-vatno-input">VAT/TIN No.</label>
                          <input type="text" class="form-control" id="verticalnav-vatno-input"
                            placeholder="Enter your VAT/TIN number">
                        </div>
                      </BCol>
                    </BRow>
                    <BRow>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="verticalnav-cstno-input">CST No.</label>
                          <input type="text" class="form-control" id="verticalnav-cstno-input"
                            placeholder="Enter your CST number">
                        </div>
                      </BCol>

                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="verticalnav-servicetax-input">Service Tax No.</label>
                          <input type="text" class="form-control" id="verticalnav-servicetax-input"
                            placeholder="Enter your Service Tax number">
                        </div>
                      </BCol>
                    </BRow>
                    <BRow>
                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="verticalnav-companyuin-input">Company UIN</label>
                          <input type="text" class="form-control" id="verticalnav-companyuin-input"
                            placeholder="Enter your Company UIN number">
                        </div>
                      </BCol>

                      <BCol lg="6">
                        <div class="mb-3">
                          <label for="verticalnav-declaration-input">Declaration</label>
                          <input type="text" class="form-control" id="verticalnav-Declaration-input"
                            placeholder="Enter your Declaration">
                        </div>
                      </BCol>
                    </BRow>
                  </form>
                </section>

                <!-- Bank Details -->
                <h3 id="vertical-example-h-2" class="title" :class="{ 'current': activeVerTab === 0 }">Bank Details</h3>
                <section id="vertical-example-p-2"
                  :class="{ 'd-block current': activeVerTab === 2, 'd-none': activeVerTab !== 2 }">
                  <div>
                    <form>
                      <BRow>
                        <BCol lg="6">
                          <div class="mb-3">
                            <label for="verticalnav-namecard-input">Name on Card</label>
                            <input type="text" class="form-control" id="verticalnav-namecard-input"
                              placeholder="Enter your Name on Card">
                          </div>
                        </BCol>

                        <BCol lg="6">
                          <div class="mb-3">
                            <label>Credit Card Type</label>
                            <select class="form-select">
                              <option selected="">Select Card Type</option>
                              <option value="AE">American Express</option>
                              <option value="VI">Visa</option>
                              <option value="MC">MasterCard</option>
                              <option value="DI">Discover</option>
                            </select>
                          </div>
                        </BCol>
                      </BRow>
                      <BRow>
                        <BCol lg="6">
                          <div class="mb-3">
                            <label for="verticalnav-cardno-input">Credit Card Number</label>
                            <input type="text" class="form-control" id="verticalnav-cardno-input"
                              placeholder="Enter your Enter Credit Card Number">
                          </div>
                        </BCol>

                        <BCol lg="6">
                          <div class="mb-3">
                            <label for="verticalnav-card-verification-input">Card Verification Number</label>
                            <input type="text" class="form-control" id="verticalnav-card-verification-input"
                              placeholder="Enter your Card Verification Number">
                          </div>
                        </BCol>
                      </BRow>
                      <BRow>
                        <BCol lg="6">
                          <div class="mb-3">
                            <label for="verticalnav-expiration-input">Expiration Date</label>
                            <input type="text" class="form-control" id="verticalnav-expiration-input"
                              placeholder="Enter your Expiration Date">
                          </div>
                        </BCol>

                      </BRow>
                    </form>
                  </div>
                </section>

                <!-- Confirm Details -->
                <h3 id="vertical-example-h-3" class="title" :class="{ 'current': activeVerTab === 0 }"> Confirm Detail
                </h3>
                <section id="vertical-example-p-3"
                  :class="{ 'd-block current': activeVerTab === 3, 'd-none': activeVerTab !== 3 }">
                  <BRow class="justify-content-center">
                    <BCol lg="6">
                      <div class="text-center">
                        <div class="mb-4">
                          <i class="mdi mdi-check-circle-outline text-success display-4"></i>
                        </div>
                        <div>
                          <h5>Confirm Detail</h5>
                          <p class="text-muted">If several languages coalesce, the grammar of the resulting</p>
                        </div>
                      </div>
                    </BCol>
                  </BRow>
                </section>
              </div>
              <div class="actions clearfix">
                <ul>
                  <li class="disabled" v-if="activeVerTab === 0">
                    <BLink href="#">Previous</BLink>
                  </li>
                  <li @click="setActiveVerTab(activeVerTab - 1)" v-if="activeVerTab > 0">
                    <BLink href="#">Previous</BLink>
                  </li>
                  <li @click="setActiveVerTab(activeVerTab + 1)" v-if="activeVerTab < 3">
                    <BLink href="#">Next</BLink>
                  </li>
                  <li v-if="activeVerTab === 3">
                    <BLink href="#">Finish</BLink>
                  </li>
                </ul>
              </div>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>
  </Layout>
</template>
