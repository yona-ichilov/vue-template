<script>
import { onMounted } from 'vue'

 const Forecast = [{id:3,name:"great test",email:"test@tets.com"}]
  
export default {
 
  setup() {

    onMounted(() => {

      // need to check why he cant get to the server
     fetch('http://localhost:5144/WeatherForecast', {
        headers: {Authorization: 'Bearer 1c7163d5-63d3-4b24-bf97-a6b13160026e'}
      })
                          .then(response =>{
                            debugger
                              return response.json()
                          })
                          .then(data => {
                              Forecast = data; // Update the users array with fetched data
                          })
                          .catch(error => {
                              console.error('Error fetching data:', error);
                          });
      })

    return {
      Forecast
    }
  }
}

 

</script>

<template>
  <div class="about">
    <h1>This is an about page</h1>   
     <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Name</th>
                    <th>Email</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="frcst in Forecast" :key="frcst.id">
                    <td>{{ frcst.id }}</td>
                    <td>{{ frcst.name }}</td>
                    <td>{{ frcst.email }}</td>
                    <td>{{ frcst.date }}</td>
                    <td>{{ frcst.temperatureC }}</td>
                    <td>{{ frcst.temperatureF }}</td>
                    <td>{{ frcst.summary }}</td>
                </tr>
            </tbody>
        </table>
  </div>
 
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
