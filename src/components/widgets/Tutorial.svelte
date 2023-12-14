<script lang="ts">
	import { COLS, ROWS } from "../../utils";

	import { Tile } from "../board";
	export let visible: boolean;
</script>

<h3>玩法教程</h3>
<div>
	尝试 {ROWS} 次猜出单词，每次猜测必须是包含 {COLS} 个字母的有效单词，
	每次猜测后，图块的颜色都会改变，表示您的猜测与该单词的接近程度。
</div>
<div class:complete={visible} class="examples">
	<div><strong>示例</strong></div>
	<div class="row">
		<Tile value="w" state="🟩" />
		<Tile value="e" state="🔳" />
		<Tile value="a" state="🔳" />
		<Tile value="r" state="🔳" />
		<Tile value="y" state="🔳" />
	</div>
	<div>🟩 表示：单词中包含字母 <strong>W</strong> 并且位置正确</div>
	<div class="row">
		<Tile value="p" state="🔳" />
		<Tile value="i" state="🟨" />
		<Tile value="l" state="🔳" />
		<Tile value="l" state="🔳" />
		<Tile value="s" state="🔳" />
	</div>
	<div>🟨 表示：单词中包含字母 <strong>I</strong> 但是不在这个位置</div>
	<div class="row">
		<Tile value="v" state="🔳" />
		<Tile value="a" state="🔳" />
		<Tile value="g" state="🔳" />
		<Tile value="u" state="⬛" />
		<Tile value="e" state="🔳" />
	</div>
	<div>⬛ 表示：单词中不包含字母 <strong>U</strong></div>
	<div class="row">
		<Tile value="w" state="🟩" />
		<Tile value="h" state="🟩" />
		<Tile value="i" state="🟩" />
		<Tile value="t" state="🟩" />
		<Tile value="e" state="🟩" />
	</div>
	<div>当所有字母和位置都正确时，所有字母都显示为 🟩，挑战成功！</div>
	<div>尽可能使用最少的次数猜到它~</div>
</div>
<div>
	这是 Josh Wardle 创作的原版 <a href="https://www.nytimes.com/games/wordle/" target="_blank" rel="noreferrer">Wordle</a> 的重现版，
	具有额外的模式和功能，让您可以玩无限的单词。 
	切换到无限模式即可无限次玩。
	<br /><br />
	打开设置菜单可查看一些附加功能。
	<br /><br />
	由 <a href="https://github.com/MikhaD" target="_blank" rel="noreferrer">MikhaD</a> 使用 Svelte 用 Typescript 编写。
	<br /><br />
	由 <a href="https://github.com/angelofan" target="_blank" rel="noreferrer">Angelo Fan</a> 翻译为简体中文。
</div>

<style lang="scss">
	div {
		margin: 14px 0;
	}
	.examples {
		border-top: 1px solid var(--border-primary);
		border-bottom: 1px solid var(--border-primary);
		:global(.row > *) {
			height: 100%;
			aspect-ratio: 1;
		}
		&:not(.complete) :global(.row .back) {
			transition-delay: 0.3s;
		}
	}
	.row {
		height: 40px;
		display: flex;
		gap: 4px;
	}
</style>
