<script>
import Layout from "../../../layouts/main";
import PageHeader from "@/components/page-header";
import appConfig from "@/app.config";

import Basic from "./basic";
import Boundary from "./boundary";
import Icons from "./icons";
import Geometry from "./geometry";
import Markers from "./markers";

/**
 * Leaflet-map component
 */
export default {
  page: {
    title: "Leaflet Map",
    meta: [
      {
        name: "description",
        content: appConfig.description,
      },
    ],
  },
  components: {
    Boundary,
    Icons,
    Basic,
    Geometry,
    Markers,
    Layout,
    PageHeader,
  },
  data() {
    return {
      title: "Leaflet Maps",
      items: [
        {
          text: "Maps",
          href: "/",
        },
        {
          text: "Leaflet Maps",
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
    <BRow>
      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <h4 class="card-title mb-4">Example</h4>
            <Basic />
          </BCardBody>
        </BCard>
      </BCol>
      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <h4 class="card-title mb-4">Fixed Bounds</h4>
            <Boundary />
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>

    <BRow>
      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <h4 class="card-title mb-4">Custom Icon Example</h4>
            <Icons />
          </BCardBody>
        </BCard>
      </BCol>
      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <h4 class="card-title mb-4">Geometry Example</h4>
            <Geometry />
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>

    <BRow>
      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <h4 class="card-title mb-4">Draggable marker</h4>
            <Markers />
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>
  </Layout>
</template>
