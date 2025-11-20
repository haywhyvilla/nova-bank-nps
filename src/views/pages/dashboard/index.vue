<script>
import Layout from "../../layouts/main";
import PageHeader from "@/components/page-header";

import Stat from "@/components/widgets/stat";
import SalesAnalytics from "./sales-analytics";
import SellingProduct from './selling-product';
import TopUsers from './top-users';
import Activity from './activity';
import SocialSource from './social-source';

export default {
  components: {
    Layout,
    PageHeader,
    Stat,
    SalesAnalytics,
    SellingProduct,
    TopUsers,
    Activity,
    SocialSource
  },
  data() {
    return {
      title: "Dashboard",
      items: [
        {
          text: "Minible",
        },
        {
          text: "Dashboard",
          active: true,
        },
      ],
    };
  },
};
</script>

<template>
  <Layout>
    <PageHeader :title="title" :items="items" />
    <Stat />
    <BRow>
      <SalesAnalytics />
      <BCol xl="4">
        <BCard no-body class="bg-primary">
          <BCardBody>
            <BRow class="align-items-center">
              <BCol sm="8">
                <p class="text-white font-size-18">
                  Enhance your
                  <b>Campaign</b> for better outreach
                  <i class="mdi mdi-arrow-right"></i>
                </p>
                <div class="mt-4">
                  <BLink href="javascript: void(0);" class="btn btn-success waves-effect waves-light">Upgrade Account!</BLink>
                </div>
              </BCol>
              <BCol sm="4">
                <div class="mt-4 mt-sm-0">
                  <img src="@/assets/images/setup-analytics-amico.svg" class="img-fluid" alt />
                </div>
              </BCol>
            </BRow>
          </BCardBody>
        </BCard>
        <SellingProduct />
      </BCol>
    </BRow>
    <div class="row">
      <TopUsers />
      <Activity />
      <SocialSource />
    </div>
  </Layout>
</template>