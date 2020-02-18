<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-sm">
        </div>
        <div class="col-sm tengah">
          <br>
          <h3>Pilih Provinsi</h3>
          <div class="input-group mb-4">
            <select  v-model="selectedProvice" class="custom-select" id="inputGroupSelect03" aria-label="Example select with button addon">
              <option :value="provinces.id" v-for="(provinces,index) in province" :key="index" >{{provinces.name}}</option>
            </select>
          </div>
          <h3>Pilih Kota</h3>
          <div class="input-group mb-4">
            <select  v-model="selectedCity" class="custom-select" id="inputGroupSelect03" aria-label="Example select with button addon">
              <option :value="cities.idCity" v-for="(cities,index) in citiesz" :key="index">{{cities.name}}</option>
            </select>
          </div>
          <h3>Pilih Kecamatan</h3>
          <div class="input-group mb-4">
            <select  v-model="selectedDistrict" class="custom-select" id="inputGroupSelect03" aria-label="Example select with button addon">
              <option :value="districts.idDistrict" v-for="(districts,index) in districtez" :key="index">{{districts.name}}</option>
            </select>
          </div>
        </div>
        <br>
        <div class="col-sm">
        </div>
      </div>
    </div>
    <br>
    <a href="#demo" class="btn btn-primary" data-toggle="collapse">Detail</a>
      <div id="demo" class="collapse">
        <div id="value" v-if="selectedDistrict && selectedProvice && selectedCity">
          <p>Provinsi {{provinceValue}},{{cityValue}},{{districtValue}}</p>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'App',
  components: {

  },
  data () {
    return {
      province: [
        {
          id: '1',
          name: 'Jawa Timur'
        },
        {
          id: '2',
          name: 'Jawa Tengah'
        }
      ],
      city: [
        {
          id: '1',
          idCity: '1',
          name: 'Malang'
        },
        {
          id: '1',
          idCity: '2',
          name: 'Surabaya'
        },
        {
          id: '2',
          idCity: '3',
          name: 'Semarang'
        },
        {
          id: '2',
          idCity: '4',
          name: 'Magelang'
        }
      ],
      district: [
        {
          id: '1',
          idDistrict: '1',
          name: 'Kec.Lowokwaru'
        },
        {
          id: '2',
          idDistrict: '2',
          name: 'Kec.Genteng'
        },
        {
          id: '3',
          idDistrict: '3',
          name: 'Kec.Banyumanik'
        },
        {
          id: '4',
          idDistrict: '4',
          name: 'Kec.Bandongan'
        }
      ],
      selectedDistrict: null,
      selectedProvice: null,
      selectedCity: null,
      cityValue: null,
      provinceValue: null,
      districtValue: null

    }
  },
  computed: {
    districtez () {
      if (!this.selectedProvice) {
        return
      }
      return this.district.filter(c => c.id.toLowerCase().indexOf(this.selectedCity) > -1)
    },
    citiesz () {
      if (!this.selectedProvice) {
        return
      }
      return this.city.filter(c => c.id.toLowerCase().indexOf(this.selectedProvice) > -1)
    }

  },
  methods: {
    filterCity: function () {

    }
  },
  watch: {
    selectedProvice: function () {
      var province = this.province.filter(c => c.id.toLowerCase().indexOf(this.selectedProvice) > -1)
      this.provinceValue = province[0].name
    },
    selectedCity: function () {
      var city = this.city.filter(c => c.id.toLowerCase().indexOf(this.selectedCity) > -1)
      this.cityValue = city[0].name
    },
    selectedDistrict: function () {
      var district = this.district.filter(c => c.id.toLowerCase().indexOf(this.selectedDistrict) > -1)
      this.districtValue = district[0].name
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.tengah{
  background-color: rgb(194, 245, 170);
}
</style>
