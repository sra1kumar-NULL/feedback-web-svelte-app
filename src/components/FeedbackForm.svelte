<script>
	import RatingSelect from "./RatingSelect.svelte";
    import {createEventDispatcher} from 'svelte';
import Card from "./ui/Card.svelte";
    let text='';
    let btnDisabled=true;
    let min=10;
    let message='';
    let rating =10;
    const dispatch=createEventDispatcher();
    const handleInput=()=>{
        if(text.trim().length<=min){
            message=`There must be atleat ${min} characters`
            btnDisabled=true;
        }
        else{
            message=''
            btnDisabled=false;
        }
    }
    const handleSubmit=()=>{
        dispatch('submit-feedback',{id:Math.random()*100,text:text,rating:rating})
    }
    const handleSelect=(e)=>{
        rating =parseInt(e.detail)
    }
</script>
<Card>
    <header>How would you rate your service with us ?</header>
    <RatingSelect on:rating-select={handleSelect}/>
    <form class="feedback-form" on:submit|preventDefault={handleSubmit}>
        <input type="text" class="feedback-input" placeholder="tell us something that keeps you come back" on:input={handleInput} bind:value={text}/>
        <button class="feedback-send" disabled={btnDisabled}>send</button>
    </form>
    {#if message}
        <p class="message">{message}</p>
    {/if}
</Card>
<style>
.message{
    text-align: center;
    color:#632;
    font-size: 18px;
}
.feedback-send:disabled{
    background-color: #532;
    color:blanchedalmond;
}
.feedback-send{
    background-color: antiquewhite;
    color:#632;
    border-radius: 25px;
    font-size: 17px;
    cursor: pointer;
    border:1px whitesmoke solid;
    min-width: 100px;
    margin:3px 0px;
    /* color: whitesmoke; */
}
.feedback-form{
    border-radius: 25px;
    margin: 2% 0px;
    padding:5px 5px;
    background-color: #632;
    text-align: center;
    display: flex;
    justify-content: space-between;
}
header{
    text-align: center;
    padding: 2% 0px;
    margin: auto;
    padding: auto;
    font-size: 26px;
}
.feedback-input{
    border: none;
    color:white;
    font-size: 18px;
    padding:auto;
    margin:auto;
    background: none;
    width: 80%;
    height: 40px;
}
.feedback-input::placeholder {
    color:bisque
}
.feedback-input:focus{
    border: none;
    outline: none;
}

</style>