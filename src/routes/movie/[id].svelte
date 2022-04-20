<script>
    import { onMount } from 'svelte';
    import { page } from '$app/stores';

    let movieid = $page.params.id 

    onMount(async () => {
		const res = await fetch(`https://api.themoviedb.org/3/movie/${movieid}?api_key=${import.meta.env.VITE_API_KEY}&language=en-US`);
		
        const data = await res.json();

        console.log(data)
        if(res.ok){
            return {
                props: { movie: data.results }
            }
        }
	});

</script>


