<script>
	//import PasswordStrength from './PasswordStrength.svelte'
	
	let password = '';

    
	import checkPasswordStrength from 'check-password-strength';
	
	$: strength = checkPasswordStrength.passwordStrength(password);
</script>

<div class="container">


    <label for="password"><h2>Verify your Password</h2></label>
    <input type="text" name="password" bind:value={password} />


    <div id="color-indicators">
        <span class:valid={strength.id >= 0}></span>
        <span class:valid={strength.id >= 1}></span>
        <span class:valid={strength.id >= 2}></span>
        <span class:valid={strength.id >= 3}></span>
    </div>
    <div class="option">
        <div class="text" class:valid={strength.contains.includes("lowercase")}>at least 1 Lowercase letter [a, ..z]</div>
        <div class="text" class:valid={strength.contains.includes("uppercase")}>at least 1 Uppercase letter [A, ..Z]</div>
        <div class="text" class:valid={strength.contains.includes("number")}>at least 1 Number [1, ..9]</div>
        <div class="text" class:valid={strength.contains.includes("symbol")}>Symbol</div>
    </div>
    <h1>Your password is <i>{strength.value}!</i></h1>

</div>






<style>

    :global(body){
        background-color: #d8f3dc;
    }

    @media (min-width: 480px){
        .option{
        display: flex;
        flex-direction: column;
        margin: auto;
        font-size: large;
        text-align: center;
        row-gap: 20px;
        margin-top: 2%;
        
    }

    .option > .text{
        border: 1px solid #d68c45;
        border-radius: 8px;
        padding: 8px;
        font-size: 20px;
    }

    h2{
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        font-size: x-large;
    }

    .container{
        width: 60%;
        margin: auto;
        display: flex;
        margin-top: 5%;
        flex-direction: column;
        row-gap: 8px;

        font-family: monospace;

        justify-content: center;
        justify-items: center;
        align-items: center;
        background-color: white;
        border-radius: 20px;

        border: 1px solid #469d89;

        box-shadow: 2px 8px 10px 2px #469d89;

        
    }

	#color-indicators {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		column-gap: 0.2rem;
        width: 50%;
        margin: auto;
        margin-top: 2%;

        
	}
	#color-indicators span {
			height: 20px;

            border-radius: 20px;
	}
	span.valid:nth-child(1) { background-color: red }
	span.valid:nth-child(2) { background-color: orange }
	span.valid:nth-child(3) { background-color: yellow }
	span.valid:nth-child(4) { background-color: green }






	.text.valid {
        color: white;
        background-color: green;
        border-radius: 8px;
        padding: 8px;
    }

    

	input { 
        width: 50%; 
        border-radius: 8px;
        margin: auto;
        font-size: 26px;
        border: 2px solid green;
        text-align: center;
        
    }

    }

    /**********/
    /* MOBILE */
    /**********/

    @media (max-width: 480px){
        .option{
        display: flex;
        flex-direction: column;
        margin: auto;
        font-size: large;
        text-align: center;
        row-gap: 20px;
        margin-top: 2%;
        
    }

    h2{
        font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        font-size: x-large;
    }

    .option > .text{
        border: 1px solid #d68c45;
        border-radius: 8px;
        padding: 8px;
        font-size: 15px;
        font-weight: bolder;
    }

    .container{
        width: 94%;
        margin: auto;
        display: flex;
        margin-top: 5%;
        flex-direction: column;
        row-gap: 8px;
        background-color: white;
        margin-top: 20%;
        justify-content: center;
        justify-items: center;
        align-items: center;

        border-radius: 20px;

        font-family: monospace;

        border: 1px solid #469d89;

        box-shadow: 2px 8px 10px 2px #469d89;

        
    }

	#color-indicators {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		column-gap: 6px;
        width: 80%;
        margin: auto;
        margin-top: 2%;

        
	}
	#color-indicators span {
			height: 20px;

            border-radius: 20px;
	}
	span.valid:nth-child(1) { background-color: red }
	span.valid:nth-child(2) { background-color: orange }
	span.valid:nth-child(3) { background-color: yellow }
	span.valid:nth-child(4) { background-color: green }






	.text.valid {
        color: white;
        background-color: green;
        border-radius: 8px;
        padding: 8px;
        
    }

    

	input { 
        width: 80%; 
        border-radius: 8px;
        margin: auto;
        font-size: 26px;
        border: 2px solid black;
        
    }

    h1{
        text-align: center;
    }


    }



    



</style>


