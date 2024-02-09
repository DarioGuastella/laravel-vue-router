<script>
import { store } from "../store.js"
export default {
    name: "EventDetail",
    props: ["id"],
    data() {
        return {
            store,
            event: null
        }
    },
    mounted() {
        this.event = this.store.eventList.find(item => item.id == this.id);
    }
}
</script>
<!-- user_id name date available_tickets user {id name email} -->
<template>
    <div class="container">
        <div class="row">
            <h1 class="mb-3">Nome evento: {{ event?.name }}</h1>
            <h3 class="mb-3">A cura di: {{ event?.user.name }}</h3>
            <h5 class="mb-3"> Email: {{ event?.user.email }}</h5>
            <h3 class="mb-3">Data dell'evento: {{ event?.date }}</h3>
            <h3 class="mb-3">Biglietti rimanenti: {{ event?.available_tickets }}</h3>
            <router-link :to="{ name: 'Events' }" class="btn btn-primary">
                <span>Torna alla lista eventi</span>
            </router-link>

        </div>
    </div>
</template>

<style scoped></style>