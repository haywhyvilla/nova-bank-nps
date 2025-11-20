<script>
import Layout from "../../layouts/main";
import PageHeader from "@/components/page-header";
import appConfig from "@/app.config";

/**
 * Video component
 */
export default {
  components: { Layout, PageHeader },
  page: {
    title: "Video",
    meta: [
      {
        name: "description",
        content: appConfig.description,
      },
    ],
  },
  data() {
    return {
      title: "Video",
      items: [
        {
          text: "UI Elements",
        },
        {
          text: "Video",
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
      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Responsive embed video 16:9</BCardTitle>
            <p class="card-title-desc">
              Aspect ratios can be customized with modifier classes.
            </p>

            <!-- 16:9 aspect ratio -->
            <div class="embed-responsive ratio ratio-16x9">
              <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/1y_kfWUCFDQ"></iframe>
            </div>
          </BCardBody>
        </BCard>
      </BCol>

      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Responsive embed video 21:9</BCardTitle>
            <p class="card-title-desc">
              Aspect ratios can be customized with modifier classes.
            </p>

            <!-- 21:9 aspect ratio -->
            <div class="embed-responsive ratio ratio-21x9">
              <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/1y_kfWUCFDQ"></iframe>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>

    <BRow>
      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Responsive embed video 4:3</BCardTitle>
            <p class="card-title-desc">
              Aspect ratios can be customized with modifier classes.
            </p>

            <!-- 4:3 aspect ratio -->
            <div class="embed-responsive ratio ratio-4x3">
              <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/1y_kfWUCFDQ"></iframe>
            </div>
          </BCardBody>
        </BCard>
      </BCol>

      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Responsive embed video 1:1</BCardTitle>
            <p class="card-title-desc">
              Aspect ratios can be customized with modifier classes.
            </p>

            <!-- 1:1 aspect ratio -->
            <div class="embed-responsive ratio ratio-1x1">
              <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/1y_kfWUCFDQ"></iframe>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>
  </Layout>
</template>
