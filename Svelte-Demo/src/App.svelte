<script>
  import EditForm from "./lib/EditForm.svelte";
  import AddForm from "./lib/AddForm.svelte";
  import movieData from "./assets/movieData.json";

  let orderMethod;
  let asc = true;
  let sorted = Object.entries(movieData);
  let movieToUpdate;
  let titleToUpdate;

  function updateMovie(movie) {
    movieData[titleToUpdate] = movie;
    sorted = applyOrder();
    [movieToUpdate, titleToUpdate] = [null, null];
  }

  function addMovie(title, movie) {
    movieData[title] = movie;
    sorted = applyOrder();
    [movieToUpdate, titleToUpdate] = [null, null];
  }

  function changeOrder(orderBy) {
    if (orderMethod == orderBy) {
      asc = !asc;
    } else {
      asc = true;
    }
    orderMethod = orderBy;
    sorted = applyOrder();
  }

  function applyOrder() {
    const array = Object.entries(movieData);
    switch (orderMethod) {
      case "title":
        return array.sort((a, b) => {
          const value1 = a[0].toUpperCase().replace("THE ", "");
          const value2 = b[0].toUpperCase().replace("THE ", "");
          if (value1 > value2) {
            return asc ? 1 : -1;
          } else if (value1 < value2) {
            return asc ? -1 : 1;
          } else {
            return 0;
          }
        });
      default:
        return array.sort((a, b) => {
          const value1 = a[1][orderMethod];
          const value2 = b[1][orderMethod];
          if (value1 > value2) {
            return asc ? 1 : -1;
          } else if (value1 < value2) {
            return asc ? -1 : 1;
          } else {
            return 0;
          }
        });
    }
  }

  function openForm(text) {
    console.log(text);
  }

  console.log(Object.entries(movieData));
</script>

{#if movieToUpdate}
  <div id="blur" />
{/if}
<div class="container">
  <header>Movie Data</header>
  <div class="dropdown">
    <a id="orderMethod">
      {orderMethod ? orderMethod : ""}
      {orderMethod ? (asc ? "ascending" : "decending") : ""}
    </a>
    <button class="dropbtn">Order</button>
    <div class="dropdown-content">
      <button on:click={() => changeOrder("title")}>Alphabetical</button>
      <button on:click={() => changeOrder("year")}>Year</button>
      <button on:click={() => changeOrder("rating")}>Rating</button>
      <button on:click={() => changeOrder("runtime")}>Runtime</button>
    </div>
  </div>
</div>
<div id="movies">
  <AddForm {addMovie} />

  {#each sorted as [title, movie]}
    <div class="card" id={title}>
      <p>{title}</p>
      <ul />
      <li id="{title}.plot">
        plot: {movie.plot}
      </li>
      <li id="{title}.year">year: {movie.year}</li>
      <li id="{title}.runtime">runtime: {movie.runtime}</li>
      <li id="{title}.rating">rating: {movie.rating}</li>
      <li id="{title}.cast">cast: {movie.cast}</li>
      <button
        class="btn"
        on:click={() => {
          movieToUpdate = movie;
          titleToUpdate = title;
        }}>edit</button
      >
    </div>
  {/each}
</div>
{#if movieToUpdate}
  <p>hello</p>
  <EditForm bind:movie={movieToUpdate} {updateMovie} title={titleToUpdate} />
{/if}

<style>
  #blur {
    position: fixed;
    z-index: 8;
    width: 100vw;
    height: 100vh;
    background-color: black;
    opacity: 50%;
  }

  .container {
    display: flex;
    justify-content: space-between;
    padding: 1rem;
    padding-bottom: 0px;
  }

  header {
    font-size: x-large;
  }

  #movies {
    display: flex;
    flex-direction: column;
  }

  .btn {
    position: absolute;
    right: 21px;
    bottom: 21px;
    border-radius: 10px;
    border: 0em;
    background-color: #4d5d58;
    color: rgb(255, 255, 255);
    opacity: 80%;
  }

  .btn:hover {
    opacity: 50%;
  }

  .card {
    /* Add shadows to create the "card" effect */
    position: relative;
    box-shadow: 0 4px 8px 0 rgba(96, 94, 94, 0.2);
    transition: 0.3s;
    padding: 1.5rem;
    margin: 1rem;
    background-color: rgb(10, 168, 34);
    color: white;
    border-radius: 9px;
  }

  /* On mouse-over, add a deeper shadow */
  .card:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
    /* background: rgb(85, 158, 83) */
  }

  li {
    list-style-type: none;
    padding: 0.5rem;
    padding-left: 1rem;
  }

  /* Style The Dropdown Button */
  .dropbtn {
    background-color: #4d5d58;
    color: white;
    padding: 16px;
    font-size: 16px;
    border: none;
    cursor: pointer;
  }

  /* Dropdown Content (Hidden by Default) */
  .dropdown-content {
    display: none;
    position: absolute;
    background-color: #f9f9f9;
    min-width: 160px;
    box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.2);
    z-index: 1;
    right: 0;
  }

  /* Links inside the dropdown */
  .dropdown-content button {
    color: black;
    background-color: inherit;
    text-align: left;
    padding: 12px 16px;
    text-decoration: none;
    display: block;
    width: 100%;
    border: none;
  }

  /* Change color of dropdown links on hover */
  .dropdown-content button:hover {
    background-color: #dedede;
  }

  /* Show the dropdown menu on hover */
  .dropdown:hover .dropdown-content {
    display: block;
  }

  /* Change the background color of the dropdown button when the dropdown content is shown */
  .dropdown:hover .dropbtn {
    background-color: #869286;
  }

  #filterMethod {
    padding-right: 1rem;
  }
</style>
