<template>
  <div class="animated fadeIn">
    <b-row>
      <Card card-title="Weekly Energy Usage" card-value="9.500 KWh"/>
    </b-row>
    <b-row>
      <b-col md="12">
        <b-card header="<i class='fa fa-tachometer'></i> Energy usage for location">
          <b-row>
            <b-col sm="12" lg="4" v-for="(i, col) in Math.ceil(places.length / Math.ceil(places.length / 3))" :key="i">
              <ul class="horizontal-bars">
                <li v-for="place in places.slice((i - 1) * Math.ceil(places.length / 3), i * Math.ceil(places.length / 3))">
                  <a :href="'/#/placedetail/' + place.name" class="title">{{ place.name }}</a>
                  <div class="bars">
                    <b-progress height={} class="progress-xs" :value="place.dayUsagePerc" variant="warning"></b-progress>
                    <b-progress height={} class="progress-xs" :value="place.nightUsagePerc" variant="info"></b-progress>
                  </div>
                </li>
              </ul>
            </b-col>
          </b-row>
          <b-row>
            <b-col lg="12">
              <ul class="horizontal-bars">
                <li class="legend">
                  <b-badge pill variant="warning"></b-badge>&nbsp;<small>Day</small> &nbsp;
                  <b-badge pill variant="info"></b-badge>&nbsp;<small>Night</small>
                </li>
              </ul>
            </b-col>
          </b-row>
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import Card from '../components/Card'
import axios from 'axios'

export default {
  name: 'dashboard',
  components: {
    Card
  },
  data: function () {
    return {
      places: [
        {'name': 'class1', 'dayUsagePerc': 80, 'nightUsagePerc': 20},
        {'name': 'class2', 'dayUsagePerc': 90, 'nightUsagePerc': 10},
        {'name': 'class3', 'dayUsagePerc': 95, 'nightUsagePerc': 5},
        {'name': 'class4', 'dayUsagePerc': 93, 'nightUsagePerc': 7},
        {'name': 'class5', 'dayUsagePerc': 92, 'nightUsagePerc': 8},
        {'name': 'class6', 'dayUsagePerc': 70, 'nightUsagePerc': 30},
        {'name': 'lab1', 'dayUsagePerc': 50, 'nightUsagePerc': 50},
        {'name': 'lab2', 'dayUsagePerc': 98, 'nightUsagePerc': 2},
        {'name': 'lab3', 'dayUsagePerc': 84, 'nightUsagePerc': 16},
        {'name': 'room1', 'dayUsagePerc': 100, 'nightUsagePerc': 0},
        {'name': 'room2', 'dayUsagePerc': 99, 'nightUsagePerc': 1},
        {'name': 'entrance', 'dayUsagePerc': 70, 'nightUsagePerc': 30},
        {'name': 'floor2', 'dayUsagePerc': 75, 'nightUsagePerc': 15},
        {'name': 'floor4', 'dayUsagePerc': 75, 'nightUsagePerc': 15},
        {'name': 'floor5', 'dayUsagePerc': 75, 'nightUsagePerc': 15},
        {'name': 'floor6', 'dayUsagePerc': 75, 'nightUsagePerc': 15}
      ]
      // placePerColumn: Math.ceil(places.length / 3)
    }
  },
  created  () {
    axios.get('http://127.0.0.1:8000/places/_all')
      .then((response) => {
        this.places = response.data
        console.log(response.data)
      })
    console.log(this.$appName)
  }
}
</script>
