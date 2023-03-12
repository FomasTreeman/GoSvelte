<script>
  function addMovie() {
    return true;
  }
</script>

<div class="inputForm" style="order:1000">
  <h1 style="margin-top: 0px">Add a movie</h1>
  <form>
    <label for="title">Movie title:</label><br />
    <input type="text" id="ntitle" name="title" /><br />
    <label for="plot">Plot:</label><br />
    <input type="text" id="nplot" name="plot" /><br />
    <label for="year">Year:</label><br />
    <input type="text" id="nyear" name="year" /><br />
    <label for="runtime">Runtime:</label><br />
    <input type="text" id="nruntime" name="runtime" /><br />
    <label for="rating">Rating:</label><br />
    <input type="text" id="nrating" name="rating" /><br />
    <label for="cast">Cast:</label><br />
    <input type="text" id="ncast" name="cast" /><br />
    <button on:click={addMovie} type="button" class="btn"> Submit </button>
  </form>
</div>

<style>
  .inputForm {
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
    opacity: 100%;
  }
</style>
