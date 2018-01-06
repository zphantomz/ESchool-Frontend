<template>
  <div class="animated fadeIn">
    <b-row>
      <b-col md="12">
        <b-card :header="'Energy usage for ' + PlaceId">
          <b-row>
            <b-col sm="12" lg="12">
              <div class="chart-wrapper">
                <BarChart :height="100" />
              </div>
            </b-col>
          </b-row>
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import BarChart from '../components/BarChart'
export default {
  name: 'dashboard',
  props: ['PlaceId'],
  components: {
    BarChart
  }
}
</script>
