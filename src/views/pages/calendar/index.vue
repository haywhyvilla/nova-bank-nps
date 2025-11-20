<script>
import FullCalendar from "@fullcalendar/vue3";
import dayGridPlugin from "@fullcalendar/daygrid";
import timeGridPlugin from "@fullcalendar/timegrid";
import interactionPlugin from "@fullcalendar/interaction";
import bootstrapPlugin from "@fullcalendar/bootstrap";
import listPlugin from "@fullcalendar/list";

import { required } from "@vuelidate/validators";
import useVuelidate from "@vuelidate/core";

import Swal from "sweetalert2";

import Layout from "../../layouts/main";
import PageHeader from "@/components/page-header";

import { calendarEvents, categories } from "./data-calendar";

/**
 * Calendar component
 */
export default {
  components: { FullCalendar, Layout, PageHeader },
  setup() {
    return {
      v$: useVuelidate()
    };
  },
  data() {
    return {
      title: "Calendar",
      items: [
        {
          text: "Apps",
        },
        {
          text: "Calendar",
          active: true,
        },
      ],
      calendarEvents: calendarEvents,
      calendarOptions: {
        headerToolbar: {
          left: "prev,next today",
          center: "title",
          right: "dayGridMonth,timeGridWeek,timeGridDay,listWeek",
        },
        plugins: [
          dayGridPlugin,
          timeGridPlugin,
          interactionPlugin,
          bootstrapPlugin,
          listPlugin,
        ],
        initialView: "dayGridMonth",
        themeSystem: "bootstrap",
        initialEvents: calendarEvents,
        editable: true,
        droppable: true,
        eventResizableFromStart: true,
        dateClick: this.dateClicked,
        eventClick: this.editEvent,
        eventsSet: this.handleEvents,
        weekends: true,
        selectable: true,
        selectMirror: true,
        dayMaxEvents: true,
      },
      currentEvents: [],
      showModal: false,
      isEdit: false,
      categories: categories,
      submitted: false,
      newEventData: {},
      edit: {},
      deleteId: {},
      event: {
        title: "",
        category: "",
      }
    };
  },
  validations: {
    event: {
      title: { required },
      category: { required },
    },
  },
  methods: {
    /**
     * Modal form submit
     */
    handleSubmit() {
      this.submitted = true;

      // stop here if form is invalid
      this.v$.$touch();
      if (this.v$.$invalid) {
        return;
      } else {
        const title = this.event.title;
        const category = this.event.category;

        if (this.isEdit) {
          this.submit = true;
          this.edit.setProp("title", title);
          this.edit.setProp("classNames", category);
        } else {
          let calendarApi = this.newEventData.view.calendar;

          this.currentEvents = calendarApi.addEvent({
            id: this.newEventData.length + 1,
            title,
            start: this.newEventData.date,
            end: this.newEventData.date,
            classNames: [category],
          });
          this.newEventData = {};
        }
        this.successmsg();
        this.showModal = false;
        this.isEdit = false;
      }
      this.submitted = false;
      this.event = {};
    },
    hideModal() {
      this.submitted = false;
      this.showModal = false;
      this.isEdit = false;
      this.event = {};
    },

    /**
     * Delete event
     */
    deleteEvent() {
      this.edit.remove();
      this.showModal = false;
      this.isEdit = false;
    },
    /**
     * Modal open for add event
     */
    dateClicked(info) {
      this.event = {};
      this.newEventData = info;
      this.showModal = true;
      this.isEdit = false;
    },
    /**
     * Modal open for edit event
     */
    editEvent(info) {
      this.edit = info.event;
      this.event.title = this.edit.title;
      this.event.category = this.edit.classNames[0];
      this.showModal = true;
      this.isEdit = true;
    },

    closeModal() {
      this.showModal = false;
      this.isEdit = false;
    },

    confirm() {
      Swal.fire({
        title: "Are you sure?",
        text: "You won't be able to delete this!",
        icon: "warning",
        showCancelButton: true,
        confirmButtonColor: "#34c38f",
        cancelButtonColor: "#f46a6a",
        confirmButtonText: "Yes, delete it!",
      }).then((result) => {
        if (result.value) {
          this.deleteEvent();
          Swal.fire("Deleted!", "Event has been deleted.", "success");
        }
      });
    },

    /**
     * Show list of events
     */
    handleEvents(events) {
      this.currentEvents = events;
    },

    /**
     * Show successfull Save Dialog
     */
    successmsg() {
      Swal.fire({
        position: "center",
        icon: "success",
        title: "Event has been saved",
        showConfirmButton: false,
        timer: 1000,
      });
    },
  },
};
</script>

<template>
  <Layout>
    <PageHeader :title="title" :items="items" />
    <BRow>
      <BCol cols="12">
        <BCard no-body>
          <BCardBody>
            <div class="app-calendar">
              <FullCalendar ref="fullCalendar" :options="calendarOptions"></FullCalendar>
            </div>
          </BCardBody>
        </BCard>
      </BCol>
    </BRow>

    <!-- Add/Update Modal -->
    <BModal v-model="showModal" :title="isEdit ? 'Edit Event' : 'Add New Event'" title-class="text-black font-18"
      hide-footer body-class="p-3">
      <BForm @submit.prevent="handleSubmit">
        <BRow>
          <BCol cols="12">
            <div class="mb-3">
              <label for="name" class="form-label">Event Name</label>
              <input id="name" v-model="event.title" type="text" class="form-control" placeholder="Insert Event name"
                :class="{ 'is-invalid': submitted && v$.event.title.$error }" />
              <div v-if="submitted && !v$.event.title.required" class="invalid-feedback">
                This value is required.
              </div>
            </div>
          </BCol>
          <BCol cols="12">
            <div class="mb-3">
              <label class="control-label form-label">Category</label>
              <select v-model="event.category" class="form-control" name="category"
                :class="{ 'is-invalid': submitted && v$.event.category.errors }">
                <option v-for="option in categories" :key="option.backgroundColor" :value="`${option.value}`">
                  {{ option.name }}
                </option>
              </select>
              <div v-if="submitted && !v$.event.category.required" class="invalid-feedback">
                This value is required.
              </div>
            </div>
          </BCol>
        </BRow>
        <div class="text-end p-3">
          <BButton variant="light" @click="hideModal">Close</BButton>
          <BButton class="ms-1" variant="danger" @click="confirm" v-if="isEdit">Delete</BButton>
          <BButton type="submit" class="ms-1" variant="success">{{ isEdit ? "Save" : "Create event" }}</BButton>
        </div>
      </BForm>
    </BModal>
  </Layout>
</template>
