<input type="text" placeholder="search here.." on:input={({ target: { value } }) => debounce(value,getCountiesInfo)}>

<script>
    import { loading, responseCountries } from "./store/store";

    let timer;

    const getCountiesInfo = async (input)=> {
        loading.set(true)
        try {
            const url = `https://restcountries.eu/rest/v2/name/${input ? input: 'all'}` 
            const res = await fetch(url)
            const result = await res.json()
            console.log(result)
            console.log(Array.isArray(result))
            console.log('on success')
            responseCountries.set(result)
            console.log($responseCountries)
        } 
        catch (err){
            console.log('in catch err')
        }
        finally {
            loading.set(false)
        } 
    }

    const debounce = (v,callbackFn) => {
		clearTimeout(timer);
		timer = setTimeout(() => {
            callbackFn(v)
		}, 750);
	}
</script>