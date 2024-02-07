<script>
import { store } from '../store';
export default {
    name: "AppEventList",
    data() {
        return {
            store
        }
    }
}
</script>


<template>
    <section>
        <h1>Eventi in programma:</h1>
        <div class="container">
            <div class="row">
                <div class="col-md-4 gy-4" v-for="event in store.eventList">
                    <div class="card " style="height: 100%;">
                        <div class="card-body">
                            <h5 class="card-title">{{ event.name }}</h5>
                            <p class="card-text">Biglietti disponibili: {{ event.available_tickets }}</p>
                            <a href="#" class="btn btn-primary">Apri dettagli evento</a>
                            <a href="#" class="btn btn-warning ms-2">Compra biglietti</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>
