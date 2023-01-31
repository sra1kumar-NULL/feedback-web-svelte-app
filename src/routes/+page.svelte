<script>
	import FeedbackForm from "../components/FeedbackForm.svelte";
    import FeedbackList from "../components/FeedbackList.svelte";
	import FeedbackStats from "../components/FeedbackStats.svelte";
    let feedback=[
        {id:1,
        rating:10,
        text:'commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. In enim justo, rhoncus ut, imperdiet a, venenatis vitae, justo. Nullam dictum felis eu pede mollis pretium. '},
        {id:2,rating:8,text:'Integer tincidunt. Cras dapibus. Vivamus elementum semper nisi. Aenean vulputate eleifend tellus. Aenean leo ligula, porttitor eu, consequat vitae, eleifend ac, enim. Aliquam lorem ante, dapibus in, viverra quis, feugiat a, tellus. Phasellus viverra nulla ut metus varius laoreet. Quisque rutrum. Aenean imperdiet. Etiam ultricies nisi vel augue. Curabitur ullamcorper'},
        {id:3,rating:7,text:'Etiam rhoncus. Maecenas tempus, tellus eget condimentum rhoncus, sem quam semper libero, sit amet adipiscing sem neque sed ipsum. Nam quam nunc, blandit vel, luctus pulvinar, hendrerit id, lorem. Maecenas nec odio et ante tincidunt tempus. Donec vitae sapien ut libero venenatis faucibus. Nullam quis ante. Etiam sit amet orci eget eros faucibus tincidunt. '}
    ]
    const deleteFeedback=(e)=>{
        const itemId=e.detail;
        feedback=feedback.filter(item=>item.id!=itemId)
    }
    const handleSubmit=(e)=>{
        const feedItem=e.detail;
        feedback=[...feedback,feedItem];
    }
    $:count=feedback.length;
    $:average=Math.ceil(feedback.reduce((a,{rating})=>a+rating,0)/feedback.length)
</script>
<style>
    .container{
        max-width: 756px;
        color: white;
        padding: 5px 10px;
        margin:100px auto;
    }
</style>
<main class="container">
    <FeedbackForm on:submit-feedback={handleSubmit}/>
    <FeedbackStats {count} {average}/>
    <FeedbackList {feedback} on:delete-item={deleteFeedback}/>
</main>