<script>
/**
 * Selling-product component
 */
export default {};
</script>

<template>
    <BCard no-body>
        <BCardBody>
            <div class="float-end">
                <BDropdown right toggle-class="text-reset p-0" variant="white" menu-class="dropdown-menu-end">
                    <template v-slot:button-content>
                        <span class="fw-semibold">Sort By:</span>
                        <span class="text-muted">
                            Yearly
                            <i class="mdi mdi-chevron-down ms-1"></i>
                        </span>
                    </template>
                    <BDropdownItem>Monthly</BDropdownItem>
                    <BDropdownItem>Yearly</BDropdownItem>
                    <BDropdownItem>Weekly</BDropdownItem>
                </BDropdown>
            </div>

            <h4 class="card-title mb-4">Top Selling Products</h4>

            <BRow class="align-items-center no-gutters mt-3">
                <BCol sm="3">
                    <p class="text-truncate mt-1 mb-0">
                        <i class="mdi mdi-circle-medium text-primary me-2"></i> Desktops
                    </p>
                </BCol>

                <BCol sm="9">
                    <BProgress :value="52" variant="primary" class="mt-1" height="6px"></BProgress>
                </BCol>
            </BRow>

            <BRow class="align-items-center no-gutters mt-3">
                <BCol sm="3">
                    <p class="text-truncate mt-1 mb-0">
                        <i class="mdi mdi-circle-medium text-info me-2"></i> iPhones
                    </p>
                </BCol>
                <BCol sm="9">
                    <BProgress :value="45" variant="info" class="mt-1" height="6px"></BProgress>
                </BCol>
            </BRow>

            <BRow class="align-items-center no-gutters mt-3">
                <BCol sm="3">
                    <p class="text-truncate mt-1 mb-0">
                        <i class="mdi mdi-circle-medium text-success me-2"></i> Android
                    </p>
                </BCol>
                <BCol sm="9">
                    <BProgress :value="48" variant="success" class="mt-1" height="6px"></BProgress>
                </BCol>
            </BRow>

            <BRow class="align-items-center no-gutters mt-3">
                <BCol sm="3">
                    <p class="text-truncate mt-1 mb-0">
                        <i class="mdi mdi-circle-medium text-warning me-2"></i> Tablets
                    </p>
                </BCol>
                <BCol sm="9">
                    <BProgress :value="78" variant="warning" class="mt-1" height="6px"></BProgress>
                </BCol>
            </BRow>

            <BRow class="align-items-center no-gutters mt-3">
                <BCol sm="3">
                    <p class="text-truncate mt-1 mb-0">
                        <i class="mdi mdi-circle-medium text-purple me-2"></i> Cables
                    </p>
                </BCol>
                <BCol sm="9">
                    <BProgress :value="63" variant="purple" class="mt-1" height="6px"></BProgress>
                </BCol>
            </BRow>
        </BCardBody>
    </BCard>
</template>
