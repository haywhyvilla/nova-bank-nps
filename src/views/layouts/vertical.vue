<script>
// import router from "@/router";
import { layoutComputed } from "@/state/helpers";

import Topbar from "@/components/topbar";
import Sidebar from "@/components/side-bar";
import RightSidebar from "@/components/right-sidebar";
import Footer from "@/components/footer";

export default {
  data() {
    return {
      isMenuCondensed: false,
    }
  },
  components: {
    Topbar,
    Sidebar,
    RightSidebar,
    Footer,
  },
  computed: {
    ...layoutComputed,
  },
  name: "vertical",
  created() {
    document.body.removeAttribute("data-layout");
    document.body.removeAttribute("data-topbar");
  },
  methods: {
    toggleRightSidebar() {
      document.body.classList.toggle("right-bar-enabled");
    },
    hideRightSidebar() {
      document.body.classList.remove("right-bar-enabled");
    },
    toggleMenu() {
      var currentSIdebarSize = document.body.getAttribute('data-sidebar-size');

      if (window.innerWidth >= 1024 && window.innerWidth <= 1366) {
        document.body.setAttribute('data-sidebar-size', 'sm');
      }

      document.body.classList.toggle("sidebar-enable");
      if (window.screen.width >= 992) {

        if (currentSIdebarSize == null) {
          (document.body.getAttribute('data-sidebar-size') == null || document.body.getAttribute('data-sidebar-size') == "lg") ? document.body.setAttribute('data-sidebar-size', 'sm') : document.body.setAttribute('data-sidebar-size', 'lg')
        } else if (currentSIdebarSize == "md") {
          (document.body.getAttribute('data-sidebar-size') == "md") ? document.body.setAttribute('data-sidebar-size', 'sm') : document.body.setAttribute('data-sidebar-size', 'md')
        } else {
          (document.body.getAttribute('data-sidebar-size') == "sm") ? document.body.setAttribute('data-sidebar-size', 'lg') : document.body.setAttribute('data-sidebar-size', 'sm')
        }
      }

      // $('body').toggleClass('sidebar-enable');
      // if ($(window).width() >= 992) {
      //   if (currentSIdebarSize == null) {
      //     (document.body.getAttribute('data-sidebar-size') == null || document.body.getAttribute('data-sidebar-size') == "lg") ? document.body.setAttribute('data-sidebar-size', 'sm') : document.body.setAttribute('data-sidebar-size', 'lg')
      //   } else if (currentSIdebarSize == "md") {
      //     (document.body.getAttribute('data-sidebar-size') == "md") ? document.body.setAttribute('data-sidebar-size', 'sm') : document.body.setAttribute('data-sidebar-size', 'md')
      //   } else {
      //     (document.body.getAttribute('data-sidebar-size') == "sm") ? document.body.setAttribute('data-sidebar-size', 'lg') : document.body.setAttribute('data-sidebar-size', 'sm')
      //   }
      // }
      this.isMenuCondensed = !this.isMenuCondensed;
    },
  },

};
</script>

<template>
  <!-- Begin page -->
  <div id="layout-wrapper">
    <Topbar />
    <Sidebar :is-condensed="isMenuCondensed" :type="leftSidebarType" :width="layoutWidth" />
    <!-- ============================================================== -->
    <!-- Start right Content here -->
    <!-- ============================================================== -->
    <div class="main-content">
      <div class="page-content">
        <BContainer fluid>
          <slot />
        </BContainer>
      </div>
      <!-- End Page-content -->
      <Footer />
    </div>
    <!-- end main content-->
    <RightSidebar />
  </div>
</template>