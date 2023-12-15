<h2>quoodle</h2>
<div>
   {#await getQuotes()}
    <h1>loading...</h1>
   {:then data} 
    <h1>{JSON.stringify(data.content)}</h1><p>-{data.author}</p>
   {/await}
</div>
<footer>Programmer & Designer: <a href="youssefmichael.vercel.app">Youssef Michael</a></footer>
<script>
    async function getQuotes(){
        const response = await fetch("https://api.quotable.io/quotes/random");
        // console.log(response.json())
        const _data_ = await response.json();
        const quote = _data_[0];
        console.log(quote.content)
        return quote;
    }
    const data = getQuotes();
</script>