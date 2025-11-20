<script>
import Layout from "../../layouts/main";
import PageHeader from "@/components/page-header";
import appConfig from "@/app.config";

/**
 * Invoice-list component
 */
export default {
  page: {
    title: "Invoice List",
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
      title: "Invoice List",
      items: [
        {
          text: "Invoices",
        },
        {
          text: "Invoice List",
          active: true,
        },
      ],
      invoicelist: [
        {
          id: "#MN0131",
          date: "10 Jul, 2020",
          name: "Connie Franco",
          amount: "$141",
          status: "Paid",
        },
        {
          id: "#MN0130",
          date: "09 Jul, 2020",
          name: "Paul Reynolds",
          amount: "$153",
          status: "Paid",
        },
        {
          id: "#MN0129",
          date: "09 Jul, 2020",
          name: "Ronald Patterson",
          amount: "$220",
          status: "Pending",
        },
        {
          id: "#MN0128",
          date: "08 Jul, 2020",
          name: "Adella Perez",
          amount: "$175",
          status: "Paid",
        },
        {
          id: "#MN0127",
          date: "07 Jul, 2020",
          name: "Theresa Mayers",
          amount: "$160",
          status: "Paid",
        },
        {
          id: "#MN0126",
          date: "06 Jul, 2020",
          name: "Michael Wallace",
          amount: "$150",
          status: "Paid",
        },
        {
          id: "#MN0125",
          date: "05 Jul, 2020",
          name: "Oliver Gonzales",
          amount: "$165",
          status: "Pending",
        },
        {
          id: "#MN0124",
          date: "05 Jul, 2020",
          name: "David Burke",
          amount: "$170",
          status: "Paid",
        },
        {
          id: "#MN0123",
          date: "04 Jul, 2020",
          name: "Willie Verner",
          amount: "$140",
          status: "Pending",
        },
        {
          id: "#MN0122",
          date: "03 Jul, 2020",
          name: "Felix Perry",
          amount: "$155",
          status: "Paid",
        },
        {
          id: "#MN0121",
          date: "02 Jul, 2020",
          name: "Virgil Kelley",
          amount: "$165",
          status: "Paid",
        },
        {
          id: "#MN0120",
          date: "02 Jul, 2020",
          name: "Matthew Lawler",
          amount: "$170",
          status: "Pending",
        },
      ],
      totalRows: 1,
      currentPage: 1,
      perPage: 10,
      pageOptions: [10, 25, 50, 100],
      filter: null,
      filterOn: [],
      sortBy: "age",
      sortDesc: false,
      fields: [
        {
          key: "check",
          label: "",
        },
        {
          key: "id",
          label: "Invoice ID",
          sortable: true,
        },
        {
          key: "date",
          sortable: true,
        },
        {
          key: "name",
          label: "Billing Name",
          sortable: true,
        },
        {
          key: "amount",
          sortable: true,
        },
        {
          key: "status",
          label: "Status",
          sortable: true,
        },
        {
          key: "download",
          label: "Download Pdf",
        },
        "action",
      ],
    };
  },
  computed: {
    /**
     * Total no. of records
     */
    rows() {
      return this.invoicelist.length;
    },
  },
  mounted() {
    // Set the initial number of items
    this.totalRows = this.items.length;
  },
  methods: {
    /**
     * Search the table data with search input
     */
    onFiltered(filteredItems) {
      // Trigger pagination to update the number of buttons/pages due to filtering
      this.totalRows = filteredItems.length;
      this.currentPage = 1;
    },
  },
  middleware: "authentication",
};
</script>

<template>
  <Layout>
    <PageHeader :title="title" :items="items" />

    <BRow>
      <BCol md="4">
        <div>
          <BButton variant="success" class="mb-3">
            <i class="mdi mdi-plus me-1"></i> Add Invoice
          </BButton>
        </div>
      </BCol>
      <BCol md="8">
        <div class="float-end">
          <div class="form-inline mb-3">
            <div class="input-daterange input-group" data-provide="datepicker" data-date-format="dd M, yyyy" data-date-autoclose="true">
              <input type="text" class="form-control text-left" placeholder="From" name="From" />
              <input type="text" class="form-control text-left" placeholder="To" name="To" />
              <div class="input-group-append">
                <BButton variant="primary" type="button">
                  <i class="mdi mdi-filter-variant"></i>
                </BButton>
              </div>
            </div>
          </div>
        </div>
      </BCol>
    </BRow>
    <BRow>
      <BCol sm="12" md="6">
        <div id="tickets-table_length" class="dataTables_length">
          <label class="d-inline-flex align-items-center fw-normal">
            Show&nbsp;
            <BFormSelect v-model="perPage" size="sm" :options="pageOptions"></BFormSelect>&nbsp;entries
          </label>
        </div>
      </BCol>

      <BCol sm="12" md="6">
        <div id="tickets-table_filter" class="dataTables_filter text-md-end">
          <label class="d-inline-flex align-items-center fw-normal">
            Search:
            <BFormInput v-model="filter" type="search" class="form-control form-control-sm ms-2"></BFormInput>
          </label>
        </div>
      </BCol>
    </BRow>

    <!-- Table -->
    <div class="table-responsive mb-0">
      <BTable table-class="table table-centered datatable table-card-list" BThead-tr-class="bg-transparent" :items="invoicelist" :fields="fields" responsive="sm" :per-page="perPage" :current-page="currentPage" v-model:sort-by="sortBy" v-model:sort-desc="sortDesc" :filter="filter" :filter-included-fields="filterOn" @filtered="onFiltered">
        <template v-slot:cell(check)="data">
          <div class="custom-control custom-checkbox text-center">
            <input type="checkbox" class="form-check-input" :id="`contacusercheck${data.item.id}`" />
            <label class="custom-control-label" :for="`contacusercheck${data.item.id}`"></label>
          </div>
        </template>
        <template v-slot:cell(id)="data">
          <BLink href="javascript: void(0);" class="text-dark fw-bold">
            {{ data.item.id }}
          </BLink>
        </template>

        <template v-slot:cell(status)="data">
          <div class="badge rounded-pill bg-soft-success font-size-12" :class="{ 'bg-soft-warning': data.item.status === 'Pending' }">
            {{ data.item.status }}
          </div>
        </template>

        <template v-slot:cell(name)="data">
          <BLink href="#" class="text-body">{{ data.item.name }}</BLink>
        </template>
        <template v-slot:cell(download)>
          <div>
            <BButton variant="light" class="btn-sm w-xss">
              Pdf
              <i class="uil uil-download-alt ms-2"></i>
            </BButton>
          </div>
        </template>
        <template v-slot:cell(action)>
          <ul class="list-inline mb-0">
            <li class="list-inline-item">
              <BLink href="javascript:void(0);" class="px-2 text-primary" v-b-tooltip.hover title="Edit">
                <i class="uil uil-pen font-size-18"></i>
              </BLink>
            </li>
            <li class="list-inline-item">
              <BLink href="javascript:void(0);" class="px-2 text-danger" v-b-tooltip.hover title="Delete">
                <i class="uil uil-trash-alt font-size-18"></i>
              </BLink>
            </li>
          </ul>
        </template>
      </BTable>
    </div>
    <BRow>
      <BCol>
        <div class="dataTables_paginate paging_simple_numbers float-end">
          <ul class="pagination pagination-rounded">
            <!-- pagination -->
            <BPagination v-model="currentPage" :total-rows="rows" :per-page="perPage"></BPagination>
          </ul>
        </div>
      </BCol>
    </BRow>
  </Layout>
</template>
