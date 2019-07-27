<template>
    <div class="container">
        <Header :quoteCount="quotes.length" :maxQuotes="maxQuotes"/>
        <NewQuote @quoteAdded="newQuote"/>
        <QuoteGrid :quotes="quotes" @quoteDeleted="deleteQuote"/>
        <div class="row">
            <div class="col-sm-12 text-center mt-5">
                <div class="alert alert-info">
                    Información: Haz click en una Cita para eliminarla.
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue';
    import NewQuote from './components/NewQuote.vue';
    import Header from './components/Header.vue';

    export default {
        data: () => ({
            quotes: [
                'Prueba'
            ],
            maxQuotes: 10
        }),
        methods: {
            newQuote(quote) {
                if(this.quotes.length >= this.maxQuotes){
                    alert('Borre una Quote primero.');
                }else{
                    this.quotes.push(quote);
                }
                
            },
            deleteQuote(index) {
                this.quotes.splice(index, 1);
            }
        },
        components: {
            QuoteGrid,
            NewQuote,
            Header
        }
    }
</script>

<style>
</style>
