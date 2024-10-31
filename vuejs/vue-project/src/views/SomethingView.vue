<script>
let loaded = false
function clickMe() {
  alert("Not that hard !!")
}

function fetch() {
  
  setTimeout(() => {
    const element = document.querySelector("#fetching")

    if (element)
      element.innerHTML = ""

      document.querySelector("table").attributes.removeNamedItem("hidden")
      document.querySelector("#nodata").setAttribute("hidden", true)
      document.querySelector("#fetching").setAttribute("hidden", true)

  }, 3000)

  let numberOfDots = 0
  setInterval(() => {
    if (loaded)
      return;

    const element = document.querySelector("#fetching")
    
    numberOfDots++

    if (numberOfDots > 3)
      numberOfDots = 0
    if (numberOfDots === 3)
      element.innerHTML = "Fetching"
    if (numberOfDots === 0)
      element.innerHTML = "Fetching ."
    if (numberOfDots === 1)
      element.innerHTML = "Fetching .."
    if (numberOfDots === 2)
      element.innerHTML = "Fetching ..."
  }, 500)
}
fetch()

export default {
  data() {
    return {
      loaded,
      fetching: {
        fetching: "Fetching ...",
        noData: "No Data"
      },
      clickMe
    }
  }
}
</script>

<template>
  <div >
    <button @click="clickMe()">Click me</button>

    <div id="fetching">{{ fetching.fetching }}</div>

    <div id="nodata" hidden>No Data</div>
    <table hidden>
      <thead>
        <tr>          
          <th>Id</th>
          <th>Name</th>
          <th>Notes</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>1</th>
          <th>Bob Ross</th>
          <th>Painter</th>
        </tr>

        <tr>
          <th>2</th>
          <th>Chuck Norris</th>
          <th>Karate Fighter</th>
        </tr>

        <tr>
          <th>3</th>
          <th>Captain America</th>
          <th>Super-Hero</th>
        </tr>

        <tr>
          <th>4</th>
          <th>Dwayne Johnson</th>
          <th>Actor</th>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>
table td {
  font-weight: bold;
}
@media (min-width: 1024px) {
  .something {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
