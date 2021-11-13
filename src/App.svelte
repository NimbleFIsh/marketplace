<script>
	import {Route, Router} from "svelte-routing";
	import Main from "./routes/Main.svelte"
	import Notfound from "./routes/Notfound.svelte";
	import {navigate} from "svelte-routing";

	navigate('/')
</script>


<Router>
	<Route path="/">
		<Main/>
	</Route>
	<Route path="/*">
		<Notfound/>
	</Route>
</Router>

<style>
	:global(body) {
		margin: 0;
		padding: 0;
		overflow-x: hidden;
	}
</style>