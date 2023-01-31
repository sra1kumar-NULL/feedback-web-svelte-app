<script>
 import Card from "./ui/Card.svelte";
 import {createEventDispatcher} from 'svelte';
 export let item
 const dispatch=createEventDispatcher();
 const handleDelete=(itemId)=>{
    dispatch('delete-item',itemId)
 }
</script>

<Card>
  <div class="item-rating">
    {item.rating}
  </div>
  <button class="close" on:click={()=>{handleDelete(item.id)}}>
    X
  </button>
  <p class="item-text">
    {item.text}
  </p>
</Card>
<style>
    
    .item-rating{
        position: absolute;
        top:-10px;
        left:-15px;
        background-color: bisque;
        color:brown;
        width:25px;
        height:25px;
        text-align: center;
        padding:10px;
        font-size: 19px;
        border: 1px #664433 solid;
        border-radius: 50%;
    }
    .item-text{
        padding: auto;
    }
    .close{
        position: absolute;
        top:2px;
        right:2px;
        font-size: 17px;
        color:black;
        border:none;
        cursor: pointer;
        background: none;
    }
</style>