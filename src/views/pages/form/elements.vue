<script>
import Layout from "../../layouts/main";
import PageHeader from "@/components/page-header";
import appConfig from "@/app.config";

/**
 * Elements component
 */
export default {
  page: {
    title: "Basic Elements",
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
      title: "Basic Elements",
      items: [
        {
          text: "Forms",
          href: "/",
        },
        {
          text: "Basic Elements",
          active: true,
        },
      ],
      checked: true,
      smchecked: true,
      lgchecked: true,
      selectedToogle: "A",
      selectedDefault: "a",
      rightcheck: "accepted",
      status: "accepted",
      exManualSelected: null,
    };
  },
  middleware: "authentication",
};
</script>

<template>
  <Layout>
    <PageHeader :title="title" :items="items" />
    <BRow>
      <BCol cols="12">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Textual inputs</BCardTitle>
            <p class="card-title-desc">
              Here are examples of
              <code>.form-control</code> applied to each textual HTML5
              <code>&lt;input&gt;</code>
              <code>type</code>.
            </p>

            <BRow>
              <BCol cols="12">
                <BForm class="form-horizontal" role="form">
                  <BFormGroup class="mb-3" id="example text" label-cols-sm="2" label-cols-lg="2" label="Text" label-for="text">
                    <BFormInput for="text" placeholder="Artisanal kale"></BFormInput>
                  </BFormGroup>

                  <BFormGroup id="example-search" label-cols-sm="2" label-cols-lg="2" label="Search" label-for="search" class="mb-3">
                    <BFormInput id="search" placeholder="How do I shoot web" type="search" name="search"></BFormInput>
                  </BFormGroup>

                  <BFormGroup id="example-email" label-cols-sm="2" label-cols-lg="2" label="Email" label-for="email" class="mb-3">
                    <BFormInput id="email" placeholder="bootstrap@example.com"></BFormInput>
                  </BFormGroup>

                  <BFormGroup id="example-url" label-cols-sm="2" label-cols-lg="2" label="URL" label-for="url" class="mb-3">
                    <BFormInput id="url" placeholder="https://getbootstrap.com" type="url" name="url"></BFormInput>
                  </BFormGroup>

                  <BFormGroup id="example-tel" label-cols-sm="2" label-cols-lg="2" label="Telephone" label-for="tele" class="mb-3">
                    <BFormInput id="tele" placeholder="1-(555)-555-5555" type="tel" name="tel"></BFormInput>
                  </BFormGroup>

                  <BFormGroup id="example-password" label-cols-sm="2" label-cols-lg="2" label="Password" label-for="pwd" class="mb-3">
                    <BFormInput id="pwd" type="password" placeholder="password"></BFormInput>
                  </BFormGroup>

                  <BFormGroup id="example-number" label-cols-sm="2" label-cols-lg="2" label="Number" label-for="number" class="mb-3">
                    <BFormInput id="number" placeholder="42" type="number" name="number"></BFormInput>
                  </BFormGroup>

                  <BFormGroup id="example-date-time" label-cols-sm="2" label-cols-lg="2" label="Date and time" label-for="date-time" class="mb-3">
                    <BFormInput id="date-time" placeholder="2019-08-19T13:45:00" type="datetime-local"></BFormInput>
                  </BFormGroup>

                  <BFormGroup id="example-date" label-cols-sm="2" label-cols-lg="2" label="Date" label-for="date" class="mb-3">
                    <BFormInput id="date" placeholder="2019-08-19" type="date"></BFormInput>
                  </BFormGroup>

                  <BFormGroup id="example-month" label-cols-sm="2" label-cols-lg="2" label="Month" label-for="month" class="mb-3">
                    <BFormInput id="month" placeholder="2019-08" type="month"></BFormInput>
                  </BFormGroup>

                  <BFormGroup id="example-week" label-cols-sm="2" label-cols-lg="2" label="Week" label-for="week" class="mb-3">
                    <BFormInput id="week" placeholder="2019-W33" type="week"></BFormInput>
                  </BFormGroup>

                  <BFormGroup id="example-time" label-cols-sm="2" label-cols-lg="2" label="Time" label-for="time" class="mb-3">
                    <BFormInput id="time" placeholder="13:45:00" type="time"></BFormInput>
                  </BFormGroup>

                  <BFormGroup id="example-color" label-cols-sm="2" label-cols-lg="2" label="Color" label-for="color" class="mb-3">
                    <BFormInput id="color" type="color" name="color" placeholder="#556ee6" class="form-control form-control-color"></BFormInput>
                  </BFormGroup>

                  <BRow class="mb-3">
                    <label class="col-md-2 col-form-label">Select</label>
                    <BCol md="10">
                      <BFormSelect v-model="exManualSelected">
                        <BFormSelectOption :value="null">Select</BFormSelectOption>
                        <BFormSelectOption>Large select</BFormSelectOption>
                        <BFormSelectOption>Small select</BFormSelectOption>
                      </BFormSelect>
                    </BCol>
                  </BRow>

                  <BRow>
                    <label for="exampleDataList" class="col-md-2 col-form-label">Datalists</label>
                    <BCol md="10">
                      <input class="form-control" list="datalistOptions" id="exampleDataList" placeholder="Type to search..." />
                      <datalist id="datalistOptions">
                        <option value="San Francisco"></option>
                        <option value="New York"></option>
                        <option value="Seattle"></option>
                        <option value="Los Angeles"></option>
                        <option value="Chicago"></option>
                      </datalist>
                    </BCol>
                  </BRow>
                </BForm>
              </BCol>
            </BRow>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>

    <BRow>
      <BCol lg="12">
        <BCard no-body>
          <BCardBody>
            <BCardTitle>Form layouts</BCardTitle>
            <BRow>
              <BCol lg="5">
                <div class="mt-4">
                  <h5 class="font-size-14 mb-4">
                    <i class="mdi mdi-arrow-right text-primary me-1"></i> Form
                    groups
                  </h5>
                  <BForm>
                    <BFormGroup label="First name" label-for="formrow-firstname-input" class="mb-3">
                      <BFormInput type="text" placeholder="Enter your full name" id="formrow-firstname-input">
                      </BFormInput>
                    </BFormGroup>

                    <BRow>
                      <BCol md="6">
                        <BFormGroup label="Email" label-for="formrow-email-input" class="mb-3">
                          <BFormInput id="formrow-email-input" type="email"></BFormInput>
                        </BFormGroup>
                      </BCol>
                      <BCol md="6">
                        <BFormGroup label="Password" label-for="formrow-password-input" class="mb-3">
                          <BFormInput id="formrow-password-input" type="password"></BFormInput>
                        </BFormGroup>
                      </BCol>
                    </BRow>
                    <BFormGroup>
                      <div class="form-check">
                        <input type="checkbox" class="form-check-input" id="formrow-customCheck" />
                        <label class="form-check-label" for="formrow-customCheck">Check me out</label>
                      </div>
                    </BFormGroup>
                    <div class="d-flex flex-wrap gap-3 mt-3">
                      <BButton type="submit" class="waves-effect waves-light w-md" variant="primary">Submit</BButton>
                      <BButton type="submit" class="waves-effect waves-light w-md" variant="outline-danger">Reset
                      </BButton>
                    </div>
                  </BForm>
                </div>
              </BCol>

              <BCol lg="6" class="ms-lg-auto">
                <div class="mt-5 mt-lg-4">
                  <h5 class="font-size-14 mb-4">
                    <i class="mdi mdi-arrow-right text-primary me-1"></i>
                    Horizontal form
                  </h5>

                  <BForm>
                    <BRow class="form-group mb-4">
                      <label for="horizontal-firstname-input" class="col-sm-3 col-form-label">First name</label>
                      <div class="col-sm-9">
                        <input type="text" class="form-control" placeholder="Enter your full name" id="horizontal-firstname-input" />
                      </div>
                    </BRow>
                    <BRow class="form-group mb-4">
                      <label for="horizontal-email-input" class="col-sm-3 col-form-label">Email</label>
                      <div class="col-sm-9">
                        <input type="email" class="form-control" id="horizontal-email-input" />
                      </div>
                    </BRow>
                    <BRow class="form-group mb-4">
                      <label for="horizontal-password-input" class="col-sm-3 col-form-label">Password</label>
                      <div class="col-sm-9">
                        <input type="password" class="form-control" id="horizontal-password-input" />
                      </div>
                    </BRow>

                    <BRow class="justify-content-end">
                      <BCol sm="9">
                        <div class="form-check mb-4">
                          <input type="checkbox" class="form-check-input" id="horizontal-customCheck" />
                          <label class="form-check-label" for="horizontal-customCheck">Remember me</label>
                        </div>

                        <div class="d-flex flex-wrap gap-3 mt-3">
                          <BButton type="submit" class="waves-effect waves-light w-md" variant="primary">Submit</BButton>
                          <BButton type="submit" class="waves-effect waves-light w-md" variant="outline-danger">Reset
                          </BButton>
                        </div>
                      </BCol>
                    </BRow>
                  </BForm>
                </div>
              </BCol>
            </BRow>

            <div class="mt-4">
              <h5 class="font-size-14 mb-4">
                <i class="mdi mdi-arrow-right text-primary me-1"></i> Inline
                forms layout
              </h5>
              <BForm class="row row-cols-lg-auto gx-3 gy-2 align-items-center">
                <BCol cols="12">
                  <label class="visually-hidden" for="specificSizeInputName">Name</label>
                  <input type="text" class="form-control" id="specificSizeInputName" placeholder="Enter Name" />
                </BCol>
                <BCol cols="12">
                  <label class="visually-hidden" for="specificSizeInputGroupUsername">Username</label>
                  <div class="input-group">
                    <div class="input-group-text">@</div>
                    <input type="text" class="form-control" id="specificSizeInputGroupUsername" placeholder="Username" />
                  </div>
                </BCol>
                <BCol cols="12">
                  <div class="form-check">
                    <input class="form-check-input" type="checkbox" id="autoSizingCheck2" />
                    <label class="form-check-label" for="autoSizingCheck2">
                      Remember me
                    </label>
                  </div>
                </BCol>
                <BCol cols="12">
                  <BButton variant="primary" type="submit" class="waves-effect waves-light w-md">Submit</BButton>
                </BCol>
              </BForm>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>
    <!-- End Form Layout -->

    <!-- Start Form Sizing -->
    <BRow>
      <BCol lg="12">
        <BCard no-body class="mb-5">
          <BCardBody>
            <BCardTitle>Sizing</BCardTitle>
            <p class="card-title-desc">
              Set heights using size like
              <code>lg</code> and <code>sm</code>.
            </p>

            <BForm>
              <BRow>
                <BCol lg="6">
                  <BFormGroup>
                    <label for="default-input">Default input</label>
                    <BFormInput id="default-input" placeholder="Default input"></BFormInput>
                  </BFormGroup>
                </BCol>
              </BRow>
              <BRow>
                <BCol lg="6">
                  <BFormGroup class="mt-3">
                    <label for="form-sm-input">Form Small input</label>
                    <BFormInput id="form-sm-input" size="sm" placeholder=".form-control-sm"></BFormInput>
                  </BFormGroup>
                </BCol>

                <BCol lg="6">
                  <BFormGroup class="mt-3 mb-0">
                    <label for="form-lg-input">Form Large input</label>
                    <BFormInput id="form-lg-input" size="lg" placeholder=".form-control-lg"></BFormInput>
                  </BFormGroup>
                </BCol>
              </BRow>
            </BForm>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>
    <!-- End Form Sizing -->

    <BRow>
      <BCol xl="6">
        <BCard no-body>
          <BCardBody>
            <BCardTitle class="mb-4">Checkboxes</BCardTitle>
            <BRow>
              <BCol md="5">
                <div>
                  <h5 class="font-size-14 mb-3">
                    <i class="mdi mdi-arrow-right text-primary me-1"></i>
                    Default Checkboxes
                  </h5>
                  <BFormCheckbox value="accepted" unchecked-value="not_accepted" class="form-check-input me-2" checked plain>Form
                    Checkbox</BFormCheckbox>

                  <BFormCheckbox value="accepted" unchecked-value="not_accepted" class="form-check-input me-2" v-model="rightcheck" plain>Form
                    Checkbox checked</BFormCheckbox>
                </div>
              </BCol>
              <BCol md="6" class="ms-auto">
                <div>
                  <h5 class="font-size-14 mb-3">
                    <i class="mdi mdi-arrow-right text-primary me-1"></i> Form
                    Checkboxes Right
                  </h5>
                  <div class="form-check form-check-right mb-2">
                    <input class="form-check-input" type="checkbox" id="formCheckRight1" />
                    <label class="form-check-label" for="formCheckRight1">
                      Form Checkbox Right
                    </label>
                  </div>

                  <div class="form-check form-check-right">
                    <input class="form-check-input" type="checkbox" id="formCheckRight2" checked="" />
                    <label class="form-check-label" for="formCheckRight2">
                      Form Checkbox Right checked
                    </label>
                  </div>
                </div>
              </BCol>
            </BRow>
          </BCardBody>
        </BCard>
      </BCol>

      <BCol xl="6">
        <BCard no-body>
          <BCardBody class="mb-0">
            <BCardTitle class="mb-4">Radios</BCardTitle>
            <BRow>
              <BCol md="5">
                <div>
                  <h5 class="font-size-14 mb-3">
                    <i class="mdi mdi-arrow-right text-primary me-1"></i>Default
                    Radios
                  </h5>
                  <BFormRadio v-model="selectedDefault" class="form-check-input  me-2" value="a" plain>Form Radio
                  </BFormRadio>
                  <BFormRadio v-model="selectedDefault" class="form-check-input me-2" value="A" plain>Form Radio
                    checked</BFormRadio>
                </div>
              </BCol>

              <BCol md="6" class="ms-auto">
                <div class="form-check-right">
                  <h5 class="font-size-14 mb-3">
                    <i class="mdi mdi-arrow-right text-primary me-1"></i>Custom
                    Radios
                  </h5>
                  <div class="form-check form-check-right">
                    <BFormRadio v-model="selectedToogle" class="form-check-input " value="b" plain>
                      Form Radio Right</BFormRadio>
                  </div>
                  <BFormRadio v-model="selectedToogle" class="form-check-input" value="B" plain>
                    Form Radio Right checked</BFormRadio>
                </div>
              </BCol>
            </BRow>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>

    <BRow>
      <BCol lg="12">
        <BCard no-body>
          <BCardBody class="pb-0">
            <BCardTitle class="mb-4">Switches</BCardTitle>
            <p class="card-title-desc">
              A switch has the markup of a custom checkbox but uses the
              <code>.custom-switch</code> class to render a toggle switch.
              Switches also support the <code>disabled</code> attribute.
            </p>

            <BRow>
              <BCol md="6">
                <div>
                  <h5 class="font-size-14 mb-3">
                    <i class="mdi mdi-arrow-right text-primary me-1"></i>Switch examples
                  </h5>
                  <!-- <h5 class="font-size-14 mb-3">Switch examples</h5> -->
                  <div class="form-check form-switch mb-3" dir="ltr">
                    <input type="checkbox" class="form-check-input" id="customSwitch1" checked="" />
                    <label class="form-check-label" for="customSwitch1">Toggle this switch element</label>
                  </div>
                  <div class="form-check form-switch" dir="ltr">
                    <input type="checkbox" class="form-check-input" disabled="" id="customSwitch2" />
                    <label class="form-check-label" for="customSwitch2">Disabled switch element</label>
                  </div>
                </div>
              </BCol>
              <BCol md="6">
                <div class="mt-4 mt-md-0">
                  <h5 class="font-size-14 mb-3">
                    <i class="mdi mdi-arrow-right text-primary me-1"></i>Switch sizes
                  </h5>
                  <div class="form-check form-switch mb-3" dir="ltr">
                    <input type="checkbox" class="form-check-input" id="customSwitchsizesm" checked="" />
                    <label class="form-check-label" for="customSwitchsizesm">Small Size Switch</label>
                  </div>

                  <div class="form-check form-switch form-switch-md mb-3" dir="ltr">
                    <input type="checkbox" class="form-check-input" id="customSwitchsizemd" />
                    <label class="form-check-label" for="customSwitchsizemd">Medium Size Switch</label>
                  </div>

                  <div class="form-check form-switch form-switch-lg mb-3" dir="ltr">
                    <input type="checkbox" class="form-check-input" id="customSwitchsizelg" checked="" />
                    <label class="form-check-label" for="customSwitchsizelg">Large Size Switch</label>
                  </div>
                </div>
              </BCol>
            </BRow>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>
  </Layout>
</template>
