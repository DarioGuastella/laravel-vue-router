<script>
import AppEventsList from "./components/AppEventsList.vue";

import axios from 'axios'; //importo Axios
import { store } from "./store.js" //state management

export default {
	components: {
		AppEventsList
	},
	data() {
		return {
			store
		}
	},
	mounted() {
		this.getEventList();

		// axios.get("indirizzo").then(risultato => {
		// 	console.log(risultato);
		// }).catch(errore => {
		// 	console.error(errore);
		// });
	},
	methods: {
		getEventList() {
			let url = this.store.apiUrl + this.store.apiEventEndpoint;

			axios.get(url).then(result => {
				if (result.status === 200) {
					if (result.data.success) {
						this.store.eventList = result.data.payload;
					}
					console.error("Ops... non siamo in grado di soddisfare la richiesta.");
				} else if (result.status === 301) {
					console.error("Ops... ciò che cerchi non si trova più qui.");
				} else if (result.status === 400) {
					console.error("Ops... non riusciamo a comprendere ciò che hai richiesto.");
				} else if (result.status === 404) {
					console.error("Ops... non riusciamo a trovare ciò che hai richiesto.");
				} else if (result.status === 500) {
					console.error("Ops... ci scusiamo per l'inconveniente, stiamo spegnendo l'incendio.");
				}
			}).catch(errore => {
				console.error(errore);
			});
		}
	}
}
</script>

<template>
	<main>

		<AppEventsList />
	</main>
</template>

<style lang="scss">
// importo il foglio di stile generale dell'applicazione, non-scoped
@use './styles/general.scss';
</style>

<style scoped lang="scss">
// importo variabili
// @use './styles/partials/variables' as *;

// ...qui eventuale SCSS di App.vue
main {
	padding: 1rem;
}
</style>