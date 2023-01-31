<script>
	import { createEventDispatcher } from "svelte";
let selected=10;
    const dispatch=createEventDispatcher()
 const handleChange=(e)=>{
  selected=e.target.value;
  dispatch('rating-select',selected)
 }

</script>
<ul class="rating">
    <li>
        <input type="radio" id="num1" value="1" name="rating" on:change={handleChange} checked={selected==1}/>
        <label for="num1">1</label>
    </li>
    <li>
        <input type="radio" id="num2" value="2" name="rating" on:change={handleChange} checked={selected==2}/>
        <label for="num2">2</label>
    </li>
    <li>
        <input type="radio" id="num3" value="3" name="rating" on:change={handleChange} checked={selected==3}/>
        <label for="num3">3</label>
    </li>
    <li>
        <input type="radio" id="num4" value="4" name="rating" on:change={handleChange} checked={selected==4}/>
        <label for="num4">4</label>
    </li>
    <li>
        <input type="radio" id="num5" name="rating" value="5" on:change={handleChange} checked={selected==5}/>
        <label for="num5">5</label>
    </li>
    <li>
        <input type="radio" id="num6" name="rating" value="6" on:change={handleChange} checked={selected==6}/>
        <label for="num6">6</label>
    </li>
    <li>
        <input type="radio" id="num7" name="rating" value="7" on:change={handleChange} checked={selected==7}/>
        <label for="num7">7</label>
    </li>
    <li>
        <input type="radio" id="num8" name="rating" value="8" on:change={handleChange} checked={selected==8}/>
        <label for="num8">8</label>
    </li>
    <li>
        <input type="radio" id="num9" name="rating" value="9" on:change={handleChange} checked={selected==9}/>
        <label for="num9">9</label>
    </li>
    <li>
        <input type="radio" id="num10" name="rating" value="10" on:change={handleChange} checked={selected==10}/>
        <label for="num10">10</label>
    </li>
</ul>
<style>
.rating li{
    position: relative;
    background-color: #632;
    border-radius: 50px;
    width: 50px;
    height: 50px;
    border:1px #532 solid;
    transition: 0.3s;
    font-size: 19px;
    color: blanchedalmond;
    text-align: center;
}
.rating input{
    position: absolute;
    width: 100%;
    display: inline;
    height: 100%;
    left:-6px;
    top:-3px;
    cursor: pointer;
}
.rating label{
    cursor: pointer;
    vertical-align: middle;
    position: absolute;
    width: 95%;
    border-radius: 50px;
    height:95%;
    background-color: #632;
    left:2px;
    top:2px;
}
[type='radio']{
    opacity: 0;
}
[type='radio']:checked ~ label{
    background-color: burlywood;
    color: #632;
}
.rating{
    list-style: none;
    display: flex;
    align-items: center;
    margin: 20px 0;
    padding:0px 20px;
    justify-content: space-around;
}
</style>