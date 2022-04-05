<template> 
<div class="row"> 
    
        <div v-for="article in articles" class="col-sm-6 col-md-4 mb-5"> 
            <div class="card w-77 h-100 border-top-0 border-start-0 border-end-0 border-bottom border-5 border-success shadow"> 
                <img :src="article.urlToImage" alt="article image" class="card-img-top"/> 
                <div class="card-body"> 
                    <h5 class="card-title"> {{ article.title }} </h5> 
                    <p class="card-text"> {{ article.description }} </p> 
                </div> 
            </div> 
        </div> 
    </div>
    <form @submit.prevent="searchNews" class="d-flex flex-column justify-content-center"> 
    <div class="input-group mx-sm-3 mb-2"> 
        <label for="search" class="visually-hidden"> Search </label> 
            <input type="search" name="search" v-model="searchTerm" id="search" class="form-control mb-2 mr-sm-2" placeholder="Enter search term here"> 
            <button class="btn btn-success mb-2"> Search </button> 
     </div> 
        <p class="fs-5 fw-light text-secondary text-center">You are searching for: {{ searchTerm }} </p> 
   </form>
    </template>


<script>
export default {
    data() {
        return {
            articles: [],
            searchTerm: ''
        }
    },
    created() {
        let self = this;

        fetch('https://newsapi.org/v2/top-headlines?country=us',
{
    headers: {
        'Authorization': `Bearer ${import.meta.env.VITE_NEWSAPI_TOKEN}`
    }
})
        .then(function(response) {
            return response.json();
        })
        .then(function(data) {
            console.log(data);
            self.articles = data.articles;
        });
    },
    methods: {
        searchNews() {
            let self = this;
            fetch('https://newsapi.org/v2/everything?q='+
        self.searchTerm + '&language=en', {
    headers: {
            'Authorization': `Bearer 7d5dbbdf482149728697acc3f35e15f1`,
            }
        })
            .then(function(response) {
                return response.json();
            });
        }
    }
}
</script>