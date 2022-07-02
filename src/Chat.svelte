<script>
	import { beforeUpdate, afterUpdate } from 'svelte';


    let div;
	let autoscroll;

    let messages = [
        {sender: 'user1', message: 'text1'},
        {sender: 'user2', message: 'text2'}
    ]

    beforeUpdate(() => {
		autoscroll = div && (div.offsetHeight + div.scrollTop) > (div.scrollHeight - 20);
	});
    afterUpdate(() => {
		if (autoscroll) div.scrollTo(0, div.scrollHeight);
	});

    function handleKeydown(event) {
		if (event.key === 'Enter') {
			const message = event.target.value;
			if (!message) return;

			messages = messages.concat({
				sender: 'user',
				message
			});
            event.target.value = '';
        }
        }
</script>

<div class="chat">
    <h1 class="chat-text">Чат</h1>
    <div class="chat-window" bind:this={div}>
        {#each messages as message}
        <article>
            <span class="chat-sender">{message.sender}:</span>
        <span class="chat-message"> {message.message}</span>
    </article>
    {/each}
    </div>
    <input class="chat-input" placeholder="Напишите что-нибудь" type="text" on:keydown={handleKeydown}>
</div>