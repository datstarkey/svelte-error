<script lang="ts">
    import type {HTMLButtonAttributes} from "svelte/elements";
    type Props = HTMLButtonAttributes & {
    variant?: "primary" | "secondary" | "tertiary";
    
    stuff:boolean; 

};
    let {...props}:Props = $props();
    
</script>



<button>
    {@render props.children?.()}
</button>