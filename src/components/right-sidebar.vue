<script>
import { layoutMethods } from "@/state/helpers";
import simplebar from 'simplebar-vue';

/**
 * Right sidebar component
 */
export default {
  data() {
    return {
      config: {
        handler: this.handleRightBarClick,
        middleware: this.middleware,
        events: ["click"],
      },
      layout: this.$store ? this.$store.state.layout.layoutType : {} || {},
      width: this.$store ? this.$store.state.layout.layoutWidth : {} || {},
      topbar: this.$store ? this.$store.state.layout.topbar : {} || {},
      sidebarType: this.$store ?
        this.$store.state.layout.leftSidebarType :
        {} || {},
      loader: this.$store ? this.$store.state.layout.loader : {} || {},
      mode: this.$store ? this.$store.state.layout.mode : {} || {},
    };
  },
  components: {
    simplebar
  },
  methods: {
    ...layoutMethods,
    hide() {
      this.$parent.toggleRightSidebar();
    },
    handleRightBarClick() {
      this.$parent.hideRightSidebar();
    },
    middleware(event) {
      return event && event.target && !event.target.classList.contains("toggle-right");
    },
    changeLayout(layout) {
      this.$store.dispatch("layout/changeLayoutType", {
        layoutType: layout,
      });
    },
    changeMode(mode) {
      this.$store.dispatch("layout/changeLayoutMode", {
        mode: mode,
      });
    },
    changeType(type) {
      this.$store.dispatch("layout/changeLeftSidebarType", {
        leftSidebarType: type,
      });
    },
    changeWidth(width) {
      this.$store.dispatch("layout/changeLayoutWidth", {
        layoutWidth: width,
      });
    },
    changeTopbartype(value) {
      this.$store.dispatch("layout/changeTopbar", {
        topbar: value,
      });
    },
  },
  watch: {
    mode: {
      immediate: true,
      handler(newVal, oldVal) {
        if (newVal !== oldVal) {
          // console.log(newVal, oldVal);
          switch (newVal) {
            case "light":
              document.body.setAttribute("data-bs-theme", "light");
              break;
            case "dark":
              document.body.setAttribute("data-bs-theme", "dark");
              break;
            default:
              document.body.setAttribute("data-bs-theme", "light");
              break;
          }
        }
      },
    },
  }
};
</script>

<template>
  <div>

    <!-- Right Sidebar -->

    <div v-click-outside="config" class="right-bar">

      <simplebar class="h-100">

        <div class="rightbar-title px-3 py-4">

          <a href="javascript:void(0);" class="right-bar-toggle float-end" @click="hide">

            <i class="mdi mdi-close noti-icon"></i>

          </a>

          <h5 class="m-0">Settings</h5>

        </div>



        <div class="p-4">

          <h6 class="mb-0">Layout</h6>

          <hr class="mt-1" />

          <div class="">

            <BFormRadioGroup v-model="layout" stacked @input="changeLayout($event)" class="d-flex">

              <BFormRadio value="vertical" class="mb-1 form-check-sm ">Vertical</BFormRadio>

              <BFormRadio value="horizontal" class="mb-1 ms-1 form-check-sm" style="margin-right: 8px;">Horizontal</BFormRadio>

            </BFormRadioGroup>

          </div>

          <!-- Width -->

          <h6 class="mt-3">Width</h6>

          <hr class="mt-1" />

          <BFormRadioGroup v-model="width" stacked @input="changeWidth($event)" class="d-flex">

            <BFormRadio value="fluid" class="mb-1 form-check-sm">Fluid</BFormRadio>

            <BFormRadio value="boxed" class="mb-1 ms-1 form-check-sm" style="margin-right: 8px;">Boxed</BFormRadio>

          </BFormRadioGroup>



          <!-- mode -->

          <h6 class="mt-3">Mode</h6>

          <hr class="mt-1" />

          <BFormRadioGroup v-model="mode" stacked @input="changeMode($event)" class="d-flex">

            <BFormRadio value="light" class="mb-1 form-check-sm">Light</BFormRadio>

            <BFormRadio value="dark" class="mb-1 ms-1 form-check-sm" style="margin-right: 8px;">Dark</BFormRadio>

          </BFormRadioGroup>



          <!-- Sidebar -->

          <div v-if="layout === 'vertical'">

            <h6 class="mt-3">Sidebar color</h6>

            <hr class="mt-1" />

            <BFormRadioGroup v-model="sidebarType" stacked @input="changeType($event)">

              <BFormRadio value="dark" class="mb-1 form-check-sm">Dark</BFormRadio>

              <BFormRadio value="light" class="mb-1 form-check-sm">Light</BFormRadio>

              <BFormRadio value="colored" class="form-check-sm">Colored</BFormRadio>

            </BFormRadioGroup>

            <h6 class="mt-3">Sidebar size</h6>

            <hr class="mt-1" />

            <BFormRadioGroup v-model="sidebarType" stacked @input="changeType($event)">

              <BFormRadio value="default" class="mb-1 form-check-sm">Default</BFormRadio>

              <BFormRadio value="compact" class="mb-1 form-check-sm">Compact</BFormRadio>

              <BFormRadio value="icon" class="mb-1 form-check-sm">Icon</BFormRadio>

            </BFormRadioGroup>

          </div>



          <!-- Topbar -->

          <div v-if="layout === 'horizontal'">

            <h6 class="mt-3">Topbar</h6>

            <hr class="mt-1" />

            <BFormRadioGroup v-model="topbar" stacked @input="changeTopbartype($event)">

              <BFormRadio value="dark" class="mb-1 form-check-sm">Dark</BFormRadio>

              <BFormRadio value="light" class="mb-1 form-check-sm">Light</BFormRadio>

              <BFormRadio value="colored" class="mb-1 form-check-sm">Colored</BFormRadio>

            </BFormRadioGroup>

          </div>

        </div>

        <!-- Settings -->

        <hr class="mt-0" />

        <h6 class="text-center mb-0">Choose Layouts</h6>

        <div class="p-4">

          <div class="mb-2">

            <router-link target="_blank" to="//themes.themesbrand.com/minible/vue/v-light/">

              <img src="@/assets/images/layouts/layout-1.jpg" class="img-fluid img-thumbnail" alt />

            </router-link>

          </div>

          <div class="mb-2">

            <router-link target="_blank" to="//themes.themesbrand.com/minible/vue/v-dark/">

              <img src="@/assets/images/layouts/layout-2.jpg" class="img-fluid img-thumbnail" alt />

            </router-link>

          </div>



          <div class="mb-2">

            <router-link target="_blank" to="//themes.themesbrand.com/minible/vue/h-light/">

              <img src="@/assets/images/layouts/layout-3.jpg" class="img-fluid img-thumbnail" alt />

            </router-link>

          </div>

        </div>

      </simplebar>

      <!-- end slimscroll-menu-->

    </div>

    <!-- /Right-bar -->



    <!-- Right bar overlay-->

    <div class="rightbar-overlay"></div>

  </div>
</template>