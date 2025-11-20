<script>
import Layout from "../../layouts/main";
import PageHeader from "@/components/page-header";
import appConfig from "@/app.config";

/**
 * Timeline component
 */
export default {
  page: {
    title: "Timeline",
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
      title: "Timeline",
      items: [
        {
          text: "Utility",
          href: "/",
        },
        {
          text: "Timeline",
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
            <h4 class="card-title mb-5">Vertical Timeline</h4>
            <div class>
              <ul class="verti-timeline list-unstyled">
                <li class="event-list">
                  <div class="event-date text-primar">03 May</div>
                  <h5>Timeline event One</h5>
                  <p class="text-muted">
                    If several languages coalesce, the grammar of the resulting
                    the individual
                  </p>
                </li>
                <li class="event-list">
                  <div class="event-date text-primar">08 May</div>
                  <h5>Timeline event Two</h5>
                  <p class="text-muted">
                    Sed ut perspiciatis unde omnis iste natus error sit illo
                    inventore veritatis
                  </p>
                </li>
                <li class="event-list">
                  <div class="event-date text-primar">11 May</div>
                  <h5>Timeline event Three</h5>
                  <p class="text-muted">
                    Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut
                    odit aut fugit
                  </p>
                </li>
                <li class="event-list">
                  <div class="event-date text-primar">16 May</div>
                  <h5>Timeline event Four</h5>
                  <p class="text-muted">
                    Quis autem vel eum iure reprehenderit qui in ea voluptate
                    velit esse quam
                  </p>
                </li>
                <li class="event-list">
                  <div class="event-date text-primar">27 May</div>
                  <h5>Timeline event Five</h5>
                  <p class="text-muted">
                    Itaque earum rerum hic tenetur a sapiente delectus maiores
                    alias consequatur aut
                  </p>
                </li>
              </ul>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>
  </Layout>
</template>

<style lang="scss"></style>
