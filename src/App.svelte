<script>
	import './style.scss';
	import GameWindow from './GameWindow.svelte';
	import Chat from './Chat.svelte'
</script>


<main class="mainWindow">
	<div>
	<img class="dice-img" src='/dice.png' alt="">
	<h1 class="dice-text">Кости</h1>
	</div>
	<span class="sum-dice">Сумма ставки</span>
	<div>
	<img class="esc-block" src="/esc_block.png" alt="">
	<span class="esc-text">Закрыть меню</span>
	</div>
	<GameWindow/>
	<Chat/>
</main>

