<template>
  <b-col sm="6" lg="3">
    <b-card no-body class="bg-primary">
      <b-card-body class="pb-0">
        <b-dropdown class="float-right" variant="transparent p-0" right>
          <template slot="button-content">
            <i class="icon-settings"></i>
          </template>
          <b-dropdown-item>Action</b-dropdown-item>
          <b-dropdown-item>Another action</b-dropdown-item>
          <b-dropdown-item>Something else here...</b-dropdown-item>
          <b-dropdown-item disabled>Disabled action</b-dropdown-item>
        </b-dropdown>
        <h4 class="mb-0">{{ CardValue }}</h4>
        <p>{{ CardTitle }}</p>
      </b-card-body>
      <card-chart class="chart-wrapper px-3" style="height:70px;" height="70" />
    </b-card>
  </b-col>
</template>
<script>
import CardChart from './CardChart.vue'
export default {
  name: 'Card',
  props: ['CardTitle', 'CardValue'],
  components: {
    CardChart
  }
}
</script>