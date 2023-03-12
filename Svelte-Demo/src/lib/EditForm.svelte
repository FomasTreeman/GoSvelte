<script>
  export let movie;
  export let title;
  export let updateMovie;

  const handleSubmit = (e) => {
    const formData = new FormData(e.target);
    for (let [key, value] of formData) {
      console.log(key, value);
      movie[key] = value;
    }
    updateMovie(movie);
  };
</script>

<div class="form-popup" id="editForm">
  <h1 id="movieTitle" style="padding-bottom: 0.5rem">{title}</h1>
  <form class="form-container">
    <form on:submit|preventDefault={handleSubmit}>
      <label for="plot">Plot</label><br />
      <input type="text" id="uplot" name="plot" value={movie.plot} /><br />
      <label for="year">Year</label><br />
      <input type="text" id="uyear" name="year" value={movie.year} /><br />
      <label for="runtime">Runtime</label><br />
      <input
        type="text"
        id="uruntime"
        name="runtime"
        value={movie.runtime}
      /><br />
      <label for="rating">Rating</label><br />
      <input type="text" id="urating" name="rating" value={movie.rating} /><br
      />
      <label for="cast">Cast</label><br />
      <input type="text" id="ucast" name="cast" value={movie.cast} /><br />
      <button type="submit" class="form-btn">Make changes</button>
      <button
        type="button"
        class="form-btn cancel"
        on:click={() => (movie = null)}>Close</button
      >
    </form>
  </form>
</div>

<style>
  /* The popup form - hidden by default */
  .form-popup {
    position: fixed;
    width: 95vw;
    bottom: 15px;
    right: 15px;
    z-index: 9;
  }

  /* Add styles to the form container */
  .form-container {
    padding: 10px;
    background-color: rgb(56, 54, 54);
  }

  /* Full-width input fields */
  .form-container input[type="text"] {
    width: auto;
    padding: 15px;
    margin: 5px 0 22px 0;
    border: none;
    width: 88vw;
  }

  /* When the inputs get focus, do something */
  .form-container input[type="text"]:focus {
    background-color: #514d4d;
    outline: none;
  }

  /* Set a style for the submit/login button */
  .form-container .form-btn {
    background-color: #04aa6d;
    color: white;
    padding: 16px 20px;
    border: none;
    cursor: pointer;
    width: 100%;
    margin-bottom: 10px;
    opacity: 0.8;
  }

  /* Add a red background color to the cancel button */
  .form-container .cancel {
    background-color: red;
  }

  /* Add some hover effects to buttons */
  .form-container .form-btn:hover {
    opacity: 1;
  }
</style>
