<p>Welcome to the predictor for the Blumenwies indoor pool</p>
<script>
    import { PUBLIC_BASE_URL } from '$env/static/public';
 	import axios from "axios";

    let season;
    let precipitationMm;
    let tempMaxC;

	let visitors = '...'

	function handleSubmit() {
		let url =
            PUBLIC_BASE_URL +
            "/api/prediction/indoorpool?season=" +
            season +
            "&precipitationMm=" +
            precipitationMm +
            "&tempMaxC=" +
            tempMaxC;
        console.log(url);
        axios.get(url).then((response) => {
            price = response.data;
        });
	}
</script>
<div class="container text-center">

	<h2>How many people will visit the Blumenwies indoor swimming pool? Our model predicts that there will be {visitors} visitors</h2>

	<div class="row justify-content-md-center">
	  <div class="col col-lg-2">
		<input type="number" class="form-control" placeholder="precipitation in mm" aria-label="precipitation" bind:value={precipitationMm}>
	  </div>
	  <div class="col col-lg-2">
		<input type="number" class="form-control" placeholder="max temperature in c" aria-label="temperature" bind:value={tempMaxC}>
	  </div>
	  <div class="col col-lg-2">

		<select class="form-select" bind:value={season}>
            <option value="spring">spring</option>
            <option value="summer">summer</option>
            <option value="autumn">autumn</option>
            <option value="winter">winter</option>
		</select>
	  </div>
	  <div class="col-md-auto">
		<button type="button" class="btn btn-primary" on:click={handleSubmit}>visitor estimation</button>
	  </div>
	</div>
  </div>