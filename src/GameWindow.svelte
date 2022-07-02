<script>
    let money = 1000;
    let Randnum = 0;
    let currentSum ='btn-money1k';
    let currentMode = 'btn-mode5p';
    let player = {CreateGame: false};
    function ChangeWindow() {
        player.CreateGame = !player.CreateGame;
    }

    function Random(min,max) {
        min = 1;
        max= 12;
        Randnum = Math.floor(Math.random() * (max-min)) + min;
    }

    function MoneySwitch(count) {
        money = count;
    }
</script>

<div class="CreateGame">
    {#if player.CreateGame}
<button on:click|once={Random} class="btn-ingame">Бросить кости</button>
<div class="your-dice">
    <p class="vs-name">ВЫ</p>
    <span class="your-number">{Randnum}</span>
</div>
<div class="him-dice">
    <p class="vs-name">ПРОТИВНИК</p>
    <span class="him-number">0</span>
</div>
    {:else}
<button on:click={ChangeWindow} class="btn-cregame">Создать игру</button>
<div class="change-count__buttons">
    <button class="btn-money" class:btn-sum__active="{currentSum === 'btn-money1k'}"
    on:click="{() => currentSum = 'btn-money1k'}" on:click={() => MoneySwitch("1000")}>1k</button>
    <button class="btn-money" class:btn-sum__active="{currentSum === 'btn-money2k'}"
    on:click="{() => currentSum = 'btn-money2k'}" on:click={() => MoneySwitch("2500")}>2.5k</button>
    <button class="btn-money" class:btn-sum__active="{currentSum === 'btn-money5k'}"
    on:click="{() => currentSum = 'btn-money5k'}" on:click={() => MoneySwitch("5000")}>5k</button>
    <button class="btn-money" class:btn-sum__active="{currentSum === 'btn-money10k'}"
    on:click="{() => currentSum = 'btn-money10k'}" on:click={() => MoneySwitch("10000")}>10k</button>
    <button class="btn-money" class:btn-sum__active="{currentSum === 'btn-money50k'}"
    on:click="{() => currentSum = 'btn-money50k'}" on:click={() => MoneySwitch("50000")}>50k</button>
    <button class="btn-money" class:btn-sum__active="{currentSum === 'btn-money100k'}"
    on:click="{() => currentSum = 'btn-money100k'}" on:click={() => MoneySwitch("100000")}>100k</button>
</div>
<div class="change-mode">
    <p class="change-mode__text">Режим игры</p>
    <button class="btn-mode1p" class:btn-mode__active="{currentMode === 'btn-mode1p'}"
    on:click="{() => currentMode = 'btn-mode1p'}">1x1</button>
    <button class="btn-mode5p" class:btn-mode__active="{currentMode === 'btn-mode5p'}"
    on:click="{() => currentMode = 'btn-mode5p'}">1x1x1x1x1</button>
</div>
<div class="players-near">
    <p class="player-name__near">Игроки рядом</p>
    <div class="player-active">
    <img on:click={ChangeWindow} class="player-active__btn" href="#" src="/dice_btn.png">
    <p class="player-name player-name--active">Maks_Mironow</p>
</div>
    <p class="player-name">Albert_Mironow</p>
    <p class="player-name">Evgeny_Savosin</p>
    <p class="player-name">Gordey_Leostratov</p>
    <p class="player-name">Roman_Yarovoy</p>
    <p class="player-name">Stanislav_Shelkovskiy</p>
    <p class="player-name">Valik_Gomenuk</p>
    <p class="player-name">Stas_Dmitrienko</p>
    <p class="player-name">Anton_Ivanov</p>
    <p class="player-name">Vasiliy_Dnitriev</p>
</div>
{/if}
<span class="money-switch">₽{money}</span>
</div>