<script>
	import { goto } from '$app/navigation';
	function goto_resistor_resistance_calculator() {
		goto('/Resistor_Resistance_Calculator');
	}
</script>

<h1>Electronics Page</h1>
<button on:click={goto_resistor_resistance_calculator}>Click me</button>

