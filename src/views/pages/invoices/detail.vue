<script>
import Layout from "../../layouts/main";
import PageHeader from "@/components/page-header";
import appConfig from "@/app.config";

/**
 * Invoice Detail component
 */
export default {
  page: {
    title: "Invoice Detail",
    meta: [
      {
        name: "description",
        content: appConfig.description,
      },
    ],
  },
  components: { Layout, PageHeader },
  data() {
    return {
      title: "Invoice Detail",
      items: [
        {
          text: "Invoices",
        },
        {
          text: "Invoice Detail",
          active: true,
        },
      ],
    };
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
            <div class="invoice-title">
              <h4 class="float-end font-size-16">
                Invoice #MN0131
                <span class="badge bg-success font-size-12 ms-2">Paid</span>
              </h4>
              <div class="mb-4">
                <img src="@/assets/images/logo-dark.png" alt="logo" height="20" />
              </div>
              <div class="text-muted">
                <p class="mb-1">641 Counts Lane Wilmore, KY 40390</p>
                <p class="mb-1">
                  <i class="uil uil-envelope-alt me-1"></i> abc@123.com
                </p>
                <p><i class="uil uil-phone me-1"></i> 012-345-6789</p>
              </div>
            </div>

            <hr class="my-4" />

            <BRow>
              <BCol sm="6">
                <div class="text-muted">
                  <h5 class="font-size-16 mb-3">Billed To:</h5>
                  <h5 class="font-size-15 mb-2">Preston Miller</h5>
                  <p class="mb-1">4450 Fancher Drive Dallas, TX 75247</p>
                  <p class="mb-1">PrestonMiller@armyspy.com</p>
                  <p>001-234-5678</p>
                </div>
              </BCol>
              <BCol sm="6">
                <div class="text-muted text-sm-end">
                  <div>
                    <h5 class="font-size-16 mb-1">Invoice No:</h5>
                    <p>#MN0131</p>
                  </div>
                  <div class="mt-4">
                    <h5 class="font-size-16 mb-1">Invoice Date:</h5>
                    <p>09 Jul, 2020</p>
                  </div>
                  <div class="mt-4">
                    <h5 class="font-size-16 mb-1">Order No:</h5>
                    <p>#1123456</p>
                  </div>
                </div>
              </BCol>
            </BRow>

            <div class="py-2">
              <h5 class="font-size-15">Order summary</h5>

              <div class="table-responsive">
                <BTableSimple class="table-nowrap table-centered mb-0">
                  <BThead>
                    <BTr>
                      <BTh style="width: 70px">No.</BTh>
                      <BTh>Item</BTh>
                      <BTh>Price</BTh>
                      <BTh>Quantity</BTh>
                      <BTh class="text-end" style="width: 120px">Total</BTh>
                    </BTr>
                  </BThead>
                  <BTbody>
                    <BTr>
                      <BTh scope="row">01</BTh>
                      <BTd>
                        <h5 class="font-size-15 mb-1">
                          Nike N012 Running Shoes
                        </h5>
                        <ul class="list-inline mb-0">
                          <li class="list-inline-item">
                            Color :
                            <span class="fw-medium">Gray</span>
                          </li>
                          <li class="list-inline-item">
                            Size :
                            <span class="fw-medium">08</span>
                          </li>
                        </ul>
                      </BTd>
                      <BTd>$260</BTd>
                      <BTd>1</BTd>
                      <BTd class="text-end">$260.00</BTd>
                    </BTr>

                    <BTr>
                      <BTh scope="row">02</BTh>
                      <BTd>
                        <h5 class="font-size-15 mb-1">Adidas Running Shoes</h5>
                        <ul class="list-inline mb-0">
                          <li class="list-inline-item">
                            Color :
                            <span class="fw-medium">Black</span>
                          </li>
                          <li class="list-inline-item">
                            Size :
                            <span class="fw-medium">09</span>
                          </li>
                        </ul>
                      </BTd>
                      <BTd>$250</BTd>
                      <BTd>1</BTd>
                      <BTd class="text-end">$250.00</BTd>
                    </BTr>

                    <BTr>
                      <BTh scope="row" colspan="4" class="text-end">
                        Sub Total
                      </BTh>
                      <BTd class="text-end">$510.00</BTd>
                    </BTr>
                    <BTr>
                      <BTh scope="row" colspan="4" class="border-0 text-end">
                        Discount :
                      </BTh>
                      <BTd class="border-0 text-end">- $50.00</BTd>
                    </BTr>
                    <BTr>
                      <BTh scope="row" colspan="4" class="border-0 text-end">
                        Shipping Charge :
                      </BTh>
                      <BTd class="border-0 text-end">$25.00</BTd>
                    </BTr>
                    <BTr>
                      <BTh scope="row" colspan="4" class="border-0 text-end">
                        Tax
                      </BTh>
                      <BTd class="border-0 text-end">$13.00</BTd>
                    </BTr>
                    <BTr>
                      <BTh scope="row" colspan="4" class="border-0 text-end">
                        Total
                      </BTh>
                      <BTd class="border-0 text-end">
                        <h4 class="m-0">$498.00</h4>
                      </BTd>
                    </BTr>
                  </BTbody>
                </BTableSimple>
              </div>
              <div class="d-print-none mt-4">
                <div class="float-end">
                  <BLink href="javascript:window.print()" class="btn btn-success me-1">
                    <i class="fa fa-print"></i>
                  </BLink>
                  <BLink href="#" class="btn btn-primary w-md ms-1">Send</BLink>
                </div>
              </div>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>
  </Layout>
</template>
