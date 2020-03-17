<template>
  <f7-page name="Countries">
    <f7-navbar title="Countries" ></f7-navbar>
    <f7-subnavbar :inner="false">
      <f7-searchbar
        search-container=".search-list"
        search-in=".item-title"
      ></f7-searchbar>
    </f7-subnavbar>
    <f7-block-title>Countries with Coronavirus</f7-block-title>
    
<f7-list class="searchbar-not-found">
    <f7-list-item title="Nothing found"></f7-list-item>
  </f7-list>
<f7-list class="search-list searchbar-found" media-list inset > 
  <f7-list-item
        v-for="(country) in countries"
        :key="country.country"
        :title="Title(country)"
        :country="country"
        link="#"
        @click="test(country)"
      >
      <f7-chip outline slot="subtitle" :text="cases(country)" :color="color(country)">Infected: <span>{{country.cases}}</span></f7-chip>
      <img style="border-radius:20%;" slot="media" :src="flag(country)" width="64" /> 
  </f7-list-item>

</f7-list>
  </f7-page>
</template>
<script>
import axios from 'axios';
import urls from '../js/urls.js';

  export default {
    data() {
      return {
        products: this.$f7.data.products,
        countries: [],
        flags: urls,
        code: null,
        number: 0,
        ind: null
      };
    },
    computed: {
      Test: function() {
        if (this.number<this.countries.length){
          this.number+=1;
          console.log(this.number + ". " + this.ind);
          return this.number + ". " + this.ind;
        }
      }
    },
    created() {
        axios.get('http://corona.xoxoni.com/countries')
      .then(response => {
        // JSON responses are automatically parsed.
        this.countries = response.data
        

      })
      .catch(e => {
        this.errors.push(e)
      })
    },
    mounted() {
      this.$f7.data.mostInfectedCountry = countries[0]
    },
    methods: {
      cases(country) {
        return "Infected:  " + country.cases
      },
      flag(country) {
        this.ind = country.country
        var obj = this.flags.find(o => o.name === country.country)
        var retu = ""
        if (obj==undefined) {
          retu="http://icons.iconarchive.com/icons/icons8/windows-8/64/City-No-Camera-icon.png"
        } else {
          retu = obj.url
        }
        return retu
      },
      color(object) {
        if (object.cases>=1000) {
          return "red"
        }else if (object.cases>=200){
          return "orange"
        }else{
          return "green"
        }
      },
      test(object) {
        console.log(object.country)
        this.$f7router.navigate('/country/', {
          props: {
            foo: object,
          }
        })
      },
      Title(country){
        console.log(this.countries.indexOf(country))
        return (this.countries.indexOf(country)+1)+". "+country.country;
      }
    }
  };
</script>
