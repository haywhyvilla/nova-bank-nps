<script>
import Layout from "../../layouts/main";
import PageHeader from "@/components/page-header";
import appConfig from "@/app.config";

/**
 * Basic table component
 */
export default {
  components: { Layout, PageHeader },
  page: {
    title: "Bootstrap Basic",
    meta: [
      {
        name: "description",
        content: appConfig.description,
      },
    ],
  },
  data() {
    return {
      title: "Bootstrap Basic",
      items: [
        {
          text: "Tables",
        },
        {
          text: "Bootstrap Basic",
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
            <BCardTitle>Basic example</BCardTitle>
            <p class="card-title-desc">
              For basic styling—light padding and only horizontal dividers—add
              the base class <code>.table</code> to any
              <code>&lt;table&gt;</code>.
            </p>

            <div class="table-responsive mb-0">
              <BTableSimple class="mb-0">
                <BThead>
                  <BTr>
                    <BTh>#</BTh>
                    <BTh>First Name</BTh>
                    <BTh>Last Name</BTh>
                    <BTh>Username</BTh>
                  </BTr>
                </BThead>
                <BTbody>
                  <BTr>
                    <BTh scope="row">1</BTh>
                    <BTd>Mark</BTd>
                    <BTd>Otto</BTd>
                    <BTd>@mdo</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">2</BTh>
                    <BTd>Jacob</BTd>
                    <BTd>Thornton</BTd>
                    <BTd>@fat</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">3</BTh>
                    <BTd>Larry</BTd>
                    <BTd>the Bird</BTd>
                    <BTd>@twitter</BTd>
                  </BTr>
                </BTbody>
              </BTableSimple>
            </div>
          </BCardBody>
        </BCard>
      </BCol>

      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Dark table</BCardTitle>
            <p class="card-title-desc">
              You can also invert the colors—with light text on dark
              backgrounds—with <code>.table-dark</code>.
            </p>

            <div class="table-responsive mb-0">
              <BTableSimple class="table-dark mb-0">
                <BThead>
                  <BTr>
                    <BTh>#</BTh>
                    <BTh>First Name</BTh>
                    <BTh>Last Name</BTh>
                    <BTh>Username</BTh>
                  </BTr>
                </BThead>
                <BTbody>
                  <BTr>
                    <BTh scope="row">1</BTh>
                    <BTd>Mark</BTd>
                    <BTd>Otto</BTd>
                    <BTd>@mdo</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">2</BTh>
                    <BTd>Jacob</BTd>
                    <BTd>Thornton</BTd>
                    <BTd>@fat</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">3</BTh>
                    <BTd>Larry</BTd>
                    <BTd>the Bird</BTd>
                    <BTd>@twitter</BTd>
                  </BTr>
                </BTbody>
              </BTableSimple>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>

    <BRow>
      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Table head</BCardTitle>
            <p class="card-title-desc">
              Use one of two modifier classes to make
              <code>&lt;BThead&gt;</code>s appear light or dark gray.
            </p>

            <div class="table-responsive mb-0">
              <BTableSimple class="mb-0">
                <BThead class="table-light">
                  <BTr>
                    <BTh>#</BTh>
                    <BTh>First Name</BTh>
                    <BTh>Last Name</BTh>
                    <BTh>Username</BTh>
                  </BTr>
                </BThead>
                <BTbody>
                  <BTr>
                    <BTh scope="row">1</BTh>
                    <BTd>Mark</BTd>
                    <BTd>Otto</BTd>
                    <BTd>@mdo</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">2</BTh>
                    <BTd>Jacob</BTd>
                    <BTd>Thornton</BTd>
                    <BTd>@fat</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">3</BTh>
                    <BTd>Larry</BTd>
                    <BTd>the Bird</BTd>
                    <BTd>@twitter</BTd>
                  </BTr>
                </BTbody>
              </BTableSimple>
            </div>
          </BCardBody>
        </BCard>
      </BCol>

      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Striped rows</BCardTitle>
            <p class="card-title-desc">
              Use <code>.table-striped</code> to add zebra-striping to any table
              row within the <code>&lt;BTbody&gt;</code>.
            </p>

            <div class="table-responsive mb-0">
              <BTableSimple class="table-striped mb-0">
                <BThead>
                  <BTr>
                    <BTh>#</BTh>
                    <BTh>First Name</BTh>
                    <BTh>Last Name</BTh>
                    <BTh>Username</BTh>
                  </BTr>
                </BThead>
                <BTbody>
                  <BTr>
                    <BTh scope="row">1</BTh>
                    <BTd>Mark</BTd>
                    <BTd>Otto</BTd>
                    <BTd>@mdo</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">2</BTh>
                    <BTd>Jacob</BTd>
                    <BTd>Thornton</BTd>
                    <BTd>@fat</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">3</BTh>
                    <BTd>Larry</BTd>
                    <BTd>the Bird</BTd>
                    <BTd>@twitter</BTd>
                  </BTr>
                </BTbody>
              </BTableSimple>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>

    <BRow>
      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Bordered table</BCardTitle>
            <p class="card-title-desc">
              Add <code>.table-bordered</code> for borders on all sides of the
              table and cells.
            </p>

            <div class="table-responsive mb-0">
              <BTableSimple class="table-bordered mb-0">
                <BThead>
                  <BTr>
                    <BTh>#</BTh>
                    <BTh>First Name</BTh>
                    <BTh>Last Name</BTh>
                    <BTh>Username</BTh>
                  </BTr>
                </BThead>
                <BTableSimple>
                  <BTr>
                    <BTh scope="row">1</BTh>
                    <BTd>Mark</BTd>
                    <BTd>Otto</BTd>
                    <BTd>@mdo</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">2</BTh>
                    <BTd>Jacob</BTd>
                    <BTd>Thornton</BTd>
                    <BTd>@fat</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">3</BTh>
                    <BTd>Larry</BTd>
                    <BTd>the Bird</BTd>
                    <BTd>@twitter</BTd>
                  </BTr>
                </BTableSimple>
              </BTableSimple>
            </div>
          </BCardBody>
        </BCard>
      </BCol>

      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Borderless table</BCardTitle>
            <p class="card-title-desc">
              Add <code>.table-borderless</code> for a table without borders.
            </p>

            <div class="table-responsive mb-0">
              <BTableSimple class="table-borderless mb-0">
                <BThead>
                  <BTr>
                    <BTh>#</BTh>
                    <BTh>First Name</BTh>
                    <BTh>Last Name</BTh>
                    <BTh>Username</BTh>
                  </BTr>
                </BThead>
                <BTbody>
                  <BTr>
                    <BTh scope="row">1</BTh>
                    <BTd>Mark</BTd>
                    <BTd>Otto</BTd>
                    <BTd>@mdo</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">2</BTh>
                    <BTd>Jacob</BTd>
                    <BTd>Thornton</BTd>
                    <BTd>@fat</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">3</BTh>
                    <BTd>Larry</BTd>
                    <BTd>the Bird</BTd>
                    <BTd>@twitter</BTd>
                  </BTr>
                </BTbody>
              </BTableSimple>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>

    <BRow>
      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Hoverable rows</BCardTitle>
            <p class="card-title-desc">
              Add <code>.table-hover</code> to enable a hover state on table
              rows within a <code>&lt;BTbody&gt;</code>.
            </p>

            <div class="table-responsive mb-0">
              <BTableSimple class="table-hover mb-0">
                <BThead>
                  <BTr>
                    <BTh>#</BTh>
                    <BTh>First Name</BTh>
                    <BTh>Last Name</BTh>
                    <BTh>Username</BTh>
                  </BTr>
                </BThead>
                <BTbody>
                  <BTr>
                    <BTh scope="row">1</BTh>
                    <BTd>Mark</BTd>
                    <BTd>Otto</BTd>
                    <BTd>@mdo</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">2</BTh>
                    <BTd>Jacob</BTd>
                    <BTd>Thornton</BTd>
                    <BTd>@fat</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">3</BTh>
                    <BTd>Larry</BTd>
                    <BTd>the Bird</BTd>
                    <BTd>@twitter</BTd>
                  </BTr>
                </BTbody>
              </BTableSimple>
            </div>
          </BCardBody>
        </BCard>
      </BCol>

      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Small table</BCardTitle>
            <p class="card-title-desc">
              Add <code>.table-sm</code> to make tables more compact by cutting
              cell padding in half.
            </p>

            <div class="table-responsive mb-0">
              <BTableSimple class="table-sm m-0">
                <BThead>
                  <BTr>
                    <BTh>#</BTh>
                    <BTh>First Name</BTh>
                    <BTh>Last Name</BTh>
                    <BTh>Username</BTh>
                  </BTr>
                </BThead>
                <BTbody>
                  <BTr>
                    <BTh scope="row">1</BTh>
                    <BTd>Mark</BTd>
                    <BTd>Otto</BTd>
                    <BTd>@mdo</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">2</BTh>
                    <BTd>Jacob</BTd>
                    <BTd>Thornton</BTd>
                    <BTd>@fat</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">3</BTh>
                    <BTd>Larry</BTd>
                    <BTd>the Bird</BTd>
                    <BTd>@twitter</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">4</BTh>
                    <BTd>Mark</BTd>
                    <BTd>Otto</BTd>
                    <BTd>@mdo</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">5</BTh>
                    <BTd>Jacob</BTd>
                    <BTd>Thornton</BTd>
                    <BTd>@fat</BTd>
                  </BTr>
                </BTbody>
              </BTableSimple>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>

    <BRow>
      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Contextual classes</BCardTitle>
            <p class="card-title-desc">
              Use contextual classes to color table rows or individual cells.
            </p>

            <div class="table-responsive mb-0">
              <BTableSimple class="mb-0">
                <BThead>
                  <BTr>
                    <BTh>#</BTh>
                    <BTh>Column heading</BTh>
                    <BTh>Column heading</BTh>
                    <BTh>Column heading</BTh>
                  </BTr>
                </BThead>
                <BTbody>
                  <BTr class="table-light">
                    <BTh scope="row">1</BTh>
                    <BTd>Column content</BTd>
                    <BTd>Column content</BTd>
                    <BTd>Column content</BTd>
                  </BTr>

                  <BTr class="table-success">
                    <BTh scope="row">2</BTh>
                    <BTd>Column content</BTd>
                    <BTd>Column content</BTd>
                    <BTd>Column content</BTd>
                  </BTr>

                  <BTr class="table-info">
                    <BTh scope="row">3</BTh>
                    <BTd>Column content</BTd>
                    <BTd>Column content</BTd>
                    <BTd>Column content</BTd>
                  </BTr>

                  <BTr class="table-warning">
                    <BTh scope="row">4</BTh>
                    <BTd>Column content</BTd>
                    <BTd>Column content</BTd>
                    <BTd>Column content</BTd>
                  </BTr>

                  <BTr class="table-danger">
                    <BTh scope="row">5</BTh>
                    <BTd>Column content</BTd>
                    <BTd>Column content</BTd>
                    <BTd>Column content</BTd>
                  </BTr>
                </BTbody>
              </BTableSimple>
            </div>
          </BCardBody>
        </BCard>
      </BCol>

      <BCol lg="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Captions</BCardTitle>
            <p class="card-title-desc">
              A <code>&lt;caption&gt;</code> functions like a heading for a
              table. It helps users with screen readers to find a table and
              understand what it’s about and decide if they want to read it.
            </p>

            <div class="table-responsive mb-0">
              <BTableSimple class="mb-0">
                <caption>
                  List of users
                </caption>
                <BThead>
                  <BTr>
                    <BTh>#</BTh>
                    <BTh>First Name</BTh>
                    <BTh>Last Name</BTh>
                    <BTh>Username</BTh>
                  </BTr>
                </BThead>
                <BTbody>
                  <BTr>
                    <BTh scope="row">1</BTh>
                    <BTd>Mark</BTd>
                    <BTd>Otto</BTd>
                    <BTd>@mdo</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">2</BTh>
                    <BTd>Jacob</BTd>
                    <BTd>Thornton</BTd>
                    <BTd>@fat</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">3</BTh>
                    <BTd>Larry</BTd>
                    <BTd>the Bird</BTd>
                    <BTd>@twitter</BTd>
                  </BTr>
                </BTbody>
              </BTableSimple>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>

    <BRow>
      <BCol lg="12">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Responsive table</BCardTitle>
            <p class="card-title-desc">
              Create responsive tables by wrapping any <code>.table</code> in
              <code>.table-responsive</code>
              to make them scroll horizontally on small devices (under 768px).
            </p>

            <div class="table-responsive mb-0">
              <BTableSimple class="mb-0">
                <BThead>
                  <BTr>
                    <BTh>#</BTh>
                    <BTh>Table heading</BTh>
                    <BTh>Table heading</BTh>
                    <BTh>Table heading</BTh>
                    <BTh>Table heading</BTh>
                    <BTh>Table heading</BTh>
                    <BTh>Table heading</BTh>
                  </BTr>
                </BThead>
                <BTbody>
                  <BTr>
                    <BTh scope="row">1</BTh>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">2</BTh>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                  </BTr>
                  <BTr>
                    <BTh scope="row">3</BTh>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                    <BTd>Table cell</BTd>
                  </BTr>
                </BTbody>
              </BTableSimple>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>
  </Layout>
</template>
