<script>
    import {createEventDispatcher} from 'svelte';
    const dispatch = createEventDispatcher();

    function sayHello(){
        dispatch('message',{
            text:"inner message"
        });
    }
</script>

<button on:click={sayHello}>
	Click to say hello
</button>