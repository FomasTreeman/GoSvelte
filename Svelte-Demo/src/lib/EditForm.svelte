<script>
  function updateMovie() {
    return true;
  }
  function closeForm() {
    return true;
  }
</script>

<div class="form-popup" id="editForm">
  <h1 id="movieTitle" style="padding-bottom: 0.5rem" />
  <form class="form-container">
    <form>
      <label for="plot">Plot</label><br />
      <input type="text" id="uplot" name="plot" /><br />
      <label for="year">Year</label><br />
      <input type="text" id="uyear" name="year" /><br />
      <label for="runtime">Runtime</label><br />
      <input type="text" id="uruntime" name="runtime" /><br />
      <label for="rating">Rating</label><br />
      <input type="text" id="urating" name="rating" /><br />
      <label for="cast">Cast</label><br />
      <input type="text" id="ucast" name="cast" /><br />
      <button type="button" class="form-btn" on:click={updateMovie}
        >Make changes</button
      >
      <button type="button" class="form-btn cancel" on:click={closeForm}
        >Close</button
      >
    </form>
  </form>
</div>

<style>
  /* The popup form - hidden by default */
  .form-popup {
    display: none;
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
    background: #f1f1f1;
  }

  /* When the inputs get focus, do something */
  .form-container input[type="text"]:focus {
    background-color: #ddd;
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
  .form-container .form-btn:hover,
  .open-button:hover {
    opacity: 1;
  }
</style>
