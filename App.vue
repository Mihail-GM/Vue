<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuote"></app-header>
        <app-new-quote @quoteAdded="neqQuote"></app-new-quote>
     <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote">  </app-quote-grid>
     <div class="row">
         <div class="col-sm-12 text-center">
             <div class="alert alert-info"> Info: Click on Quote to delete it</div>
         </div>
     </div>

    </div>
</template>

<script>
    import AddQuote from './components/AddQuote.vue';
    import QuoteGrid from './components/QuoteGrid.vue';
    import Header from './components/Header.vue';
    
    export default {
        data: function() {
            return {
                quotes: [
                    'First Quote',
                ],
                maxQuote:10
            }
        },
        methods: {
            neqQuote(quote){
                if(this.quotes.length >= this.maxQuote){
                    return alert('Please delete Quotes first');
                }
                this.quotes.push(quote);
            },
            deleteQuote(index){
                this.quotes.splice(index, 1);
            }
        },
        components: {
            'app-quote-grid': QuoteGrid,
            appNewQuote: AddQuote,
            appHeader: Header
        }
    }
</script>

<style>
</style>
