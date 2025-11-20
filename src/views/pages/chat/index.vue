<script>
import Layout from "../../layouts/main";
import PageHeader from "@/components/page-header";
import appConfig from "@/app.config";
import simplebar from "simplebar-vue";

import { chatData, chatMessagesData, groupData } from "./data";
import { required } from "@vuelidate/validators";
import useVuelidate from "@vuelidate/core";

/**
 * Chat component
 */
export default {
  page: {
    title: "Chat",
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
    simplebar
  },
  setup() {
    return {
      v$: useVuelidate()
    };
  },
  data() {
    return {
      chatData: chatData,
      groupData: groupData,
      chatMessagesData: chatMessagesData,
      title: "Chat",
      items: [
        {
          text: "Apps",
        },
        {
          text: "Chat",
          active: true,
        },
      ],
      submitted: false,
      form: {
        message: "",
      },
      username: "Designers",
      member: 12,
    };
  },
  validations: {
    form: {
      message: {
        required,
      },
    },
  }, mounted() {
    var container1 = document.querySelector(
      "#chat-list .simplebar-content-wrapper"
    );
    container1?.scrollTo({ top: 500, behavior: "smooth" });

    var container2 = document.querySelector(
      "#containerElement .simplebar-content-wrapper"
    );
    container2?.scrollTo({ top: 500, behavior: "smooth" });
  },
  methods: {
    /**
     * Get the name of user
     */
    chatUsername(name) {
      this.username = name;
      this.usermessage = "Hello";

      this.chatMessagesData = [];
      this.member = null;
      const currentDate = new Date();

      this.chatMessagesData.push({
        name: this.username,
        message: this.usermessage,
        time: currentDate.getHours() + ":" + currentDate.getMinutes(),
      });
    },

    chatGroup(name, memberno, member) {
      this.username = name;
      this.member = memberno;
      this.usermessage = "Hello";
      this.chatMessagesData = [];
      const currentDate = new Date();

      this.chatMessagesData.push({
        name: member,
        message: this.usermessage,
        time: currentDate.getHours() + ":" + currentDate.getMinutes(),
      });
    },

    /**
     * Char form Submit
     */
    formSubmit() {
      this.submitted = true;

      // stop here if form is invalid
      this.v$.$touch();

      if (this.v$.$invalid) {
        return;
      } else {
        const message = this.form.message;
        const currentDate = new Date();
        this.chatMessagesData.push({
          align: "right",
          name: "Marcus",
          message,
          time: currentDate.getHours() + ":" + currentDate.getMinutes(),
        });
        this.handleScroll();
      }
      this.submitted = false;
      this.form = {};
    },
    handleScroll() {
      if (this.$refs.current.$el) {
        setTimeout(() => {
          this.$refs.current.SimpleBar.getScrollElement().scrollTop = this.$refs.current.SimpleBar.getScrollElement().scrollHeight + 1500;
        }, 500);
      }
    },
  },
};
</script>

<template>
  <Layout>
    <PageHeader :title="title" :items="items" />

    <div class="d-lg-flex mb-4">

      <BCard no-body class="chat-leftsidebar">
        <div class="p-3 px-4">
          <div class="d-flex align-items-start">
            <div class="flex-shrink-0 me-3 align-self-center">
              <img src="@/assets/images/users/avatar-4.jpg" class="avatar-xs rounded-circle" alt="">
            </div>

            <div class="flex-grow-1">
              <h5 class="font-size-16 mb-1">
                <BLink href="#" class="text-reset ">Marcus <i class="mdi mdi-circle text-success align-middle font-size-10 ms-1"></i></BLink>
              </h5>
              <p class="text-muted mb-0">Available</p>
            </div>

            <div class="flex-shrink-0">
              <BDropdown variant="link" class="chat-noti-dropdown" toggle-class="py-0" menu-class="dropdown-menu-end" no-caret>
                <template #button-content> <i class="uil uil-ellipsis-h"></i> </template>
                <BDropdownItem href="#">Profile</BDropdownItem>
                <BDropdownItem href="#">Edit</BDropdownItem>
                <BDropdownItem href="#">Add Contact</BDropdownItem>
                <BDropdownItem href="#">Setting</BDropdownItem>
              </BDropdown>
            </div>
          </div>
        </div>

        <div class="p-3">
          <div class="search-box chat-search-box">
            <div class="position-relative">
              <input type="text" class="form-control bg-light border-light rounded" placeholder="Search...">
              <i class="uil uil-search search-icon"></i>
            </div>
          </div>
        </div>

        <div class="pb-3">
          <simplebar class="chat-message-list" style="max-height: 510px">
            <div class="p-4 border-top">
              <div>
                <div class="float-end">
                  <BLink href="javascript:void(0);" class="text-primary"><i class="mdi mdi-plus"></i> New Group</BLink>
                </div>
                <h5 class="font-size-16 mb-3"><i class="uil uil-users-alt me-1"></i> Groups</h5>
                <ul class="list-unstyled chat-list group-list">
                  <li v-for="(group, index) in groupData" :key="index" @click="chatGroup(group.name, group.member, group.membername)" :class="{ active: username == group.name }">
                    <BLink href="#">
                      <div class="d-flex align-items-center">
                        <div class="flex-shrink-0 me-3">
                          <div class="avatar-xs">
                            <span v-if="!group.icon" class="avatar-title rounded-circle bg-primary-subtle text-primary"> G
                            </span>
                            <span v-if="group.icon" class="avatar-title rounded-circle bg-primary-subtle text-primary"> <i :class="`uil ${group.icon}`"></i> </span>
                          </div>
                        </div>

                        <div class="flex-grow-1">
                          <h5 class="font-size-14 mb-0">{{ group.name }}</h5>
                        </div>
                      </div>
                    </BLink>
                  </li>
                </ul>
              </div>
            </div>

            <div class="p-4 border-top">
              <div>
                <div class="float-end">
                  <BLink href="javascript:void(0);" class="text-primary"><i class="mdi mdi-plus"></i> New Contact</BLink>
                </div>
                <h5 class="font-size-16 mb-3"><i class="uil uil-user me-1"></i> Contacts</h5>

                <ul class="list-unstyled chat-list">
                  <li v-for="data of chatData" :key="data.id" @click="chatUsername(data.name)" :class="{ active: username == data.name }">
                    <BLink href="#">
                      <div class="d-flex align-items-start" :class="{ away: data.status === 'away', online: data.status === 'online', }">
                        <div class="flex-shrink-0 align-self-center me-3">
                          <div class="user-img" :class="{ away: data.status === 'away', online: data.status === 'online', }">
                            <img :src="data.image" class="rounded-circle avatar-xs" alt="" v-if="data.image">
                            <div class="avatar-xs align-self-center" v-if="!data.image">
                              <span class="avatar-title rounded-circle bg-primary-subtle text-primary">
                                {{ data.name.charAt(0) }}
                              </span>
                            </div>
                            <span class="user-status"></span>
                          </div>
                        </div>
                        <div class="flex-grow-1 overflow-hidden">
                          <h5 class="text-truncate font-size-14 mb-1">{{ data.name }}</h5>
                          <p class="text-truncate mb-0">{{ data.message }}</p>
                        </div>

                        <div class="flex-shrink-0">
                          <div class="font-size-11">{{ data.time }}</div>
                          <div class="unread-message" v-if="data.unreadMsg">
                            <span class="badge bg-danger rounded-pill">{{ data.unreadMsg }}</span>
                          </div>
                        </div>
                      </div>
                    </BLink>
                  </li>
                </ul>
              </div>
            </div>
          </simplebar>
        </div>
      </BCard>

      <div class="w-100 user-chat mt-4 mt-sm-0 ms-lg-1">
        <BCard no-body>
          <div class="p-3 px-lg-4 border-bottom">
            <BRow>
              <BCol md="4" cols="6">
                <h5 class="font-size-16 mb-1 text-truncate">
                  <BLink href="#" class="text-reset ">{{ username }}</BLink>
                </h5>
                <p class="text-muted text-truncate mb-0" v-if="member !== null"><i class="uil uil-users-alt me-1"></i> {{
                  member !== null ? member : "" }} Members</p>
              </BCol>
              <BCol md="8" cols="6">
                <ul class="list-inline user-chat-nav text-end mb-0">
                  <li class="list-inline-item">
                    <BDropdown variant="body" toggle-class="nav-btn" menu-class="dropdown-menu-end dropdown-menu-md" no-caret>
                      <template #button-content> <i class="uil uil-search"></i> </template>
                      <BForm class="p-2">
                        <div>
                          <input type="text" class="form-control rounded" placeholder="Search...">
                        </div>
                      </BForm>
                    </BDropdown>
                  </li>

                  <li class="list-inline-item">
                    <BDropdown variant="body" toggle-class="nav-btn" menu-class="dropdown-menu-end" no-caret>
                      <template #button-content> <i class="uil uil-ellipsis-h"></i> </template>
                      <BDropdownItem href="#">Profile</BDropdownItem>
                      <BDropdownItem href="#">Archive</BDropdownItem>
                      <BDropdownItem href="#">Muted</BDropdownItem>
                      <BDropdownItem href="#">Delete</BDropdownItem>
                    </BDropdown>
                  </li>

                </ul>
              </BCol>
            </BRow>
          </div>

          <div>
            <div class="chat-conversation py-3">
              <simplebar style="max-height: 495px" id="containerElement" ref="current">
                <ul class="list-unstyled mb-0 chat-conversation-message px-3" data-simplebar>
                  <li class="chat-day-title">
                    <div class="title">Today</div>
                  </li>
                  <li v-for="data of chatMessagesData" :key="data.id" :class="{ right: `${data.align}` === 'right' }">
                    <div class="conversation-list">
                      <div class="ctext-wrap">
                        <div class="ctext-wrap-content">
                          <h5 class="font-size-14 conversation-name">
                            <BLink href="#" class="text-reset ">{{ data.name }}</BLink>
                            <span class="d-inline-block font-size-12 text-muted ms-2">{{ data.time }}</span>
                          </h5>
                          <p class="mb-0"> {{ data.message }} </p>
                        </div>
                        <BDropdown variant="" class="align-self-start" no-caret>
                          <template #button-content> <i class="uil uil-ellipsis-v"></i> </template>
                          <BDropdownItem href="#">Copy</BDropdownItem>
                          <BDropdownItem href="#">Save</BDropdownItem>
                          <BDropdownItem href="#">Forward</BDropdownItem>
                          <BDropdownItem href="#">Delete</BDropdownItem>
                        </BDropdown>
                      </div>
                    </div>
                  </li>

                </ul>
              </simplebar>
            </div>
          </div>

          <div class="p-3 chat-input-section">
            <BForm @submit.prevent="formSubmit">
              <BRow>
                <BCol>
                  <div class="position-relative">
                    <input type="text" class="form-control chat-input rounded" placeholder="Enter Message..." :class="{ 'is-invalid': submitted && v$.form.message.$error }" v-model="form.message">
                    <div v-if="submitted && v$.form.message.$error" class="invalid-feedback">
                      <span v-if="!v$.form.message.required">This value is required.</span>
                    </div>
                  </div>
                </BCol>
                <BCol class="col-auto">
                  <BButton variant="primary" type="submit" class="chat-send w-md waves-effect waves-light"><span class="d-none d-sm-inline-block me-2">Send</span> <i class="mdi mdi-send float-end"></i></BButton>
                </BCol>
              </BRow>
            </BForm>
          </div>
        </BCard>
      </div>
    </div>
  </Layout>
</template>
