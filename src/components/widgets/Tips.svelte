<script context="module" lang="ts">
	const tips = [
		"您可以通过单击 单词竞猜 或向左或向右滑动棋盘来更改游戏模式。",
		"不同游戏模式的严格模式开关互不影响。",
		"双击或右键单击格子中的单词即可查看它的释义。",
		"如果您之前的猜测没有违反严格模式的规则，就可以在游戏过程中启用严格模式。",
		"如果您使用之前的所有信息，请双击或右键单击下一行，看看可以在那里还有多少个符合已给出线索的单词。",
		"因为单词是从列表中随机选择的，所以有可能再次刷新到相同的单词。",
		"当您看到左上角的刷新按钮时，表示新单词已准备就绪，点击即可刷新。",
		"每个人同时都有相同的单词。也就是说，相同的游戏模式中，你的单词 第73期 与其他人的单词 第73期 相同。",
		"本游戏的词库不可能全部包含所有现实中的单词，即可能会有实际存在的单词提示 不在单词列表中，这属于正常现象。",
		"历史游戏不会计入您的统计数据。历史游戏是指您点击指向特定游戏期数的链接。",
		"每种游戏模式只保存最新历史游戏的数据。",
	];
</script>

<script lang="ts">
	export let change: boolean;
	let index = Math.floor(tips.length * Math.random());
	$: if (change) index = Math.floor(tips.length * Math.random());

	function nextTip() {
		index = (index + 1) % tips.length;
	}
	function previousTip() {
		index = (index - 1 + tips.length) % tips.length;
	}
</script>

<div class="outer">
	<div class="number">小贴士 {index + 1}/{tips.length}</div>
	<div class="tip">{tips[index]}</div>
	<svg
		class="left"
		on:click={previousTip}
		on:keydown={previousTip}
		xmlns="http://www.w3.org/2000/svg"
		viewBox="0 0 100 100"
	>
		<path d="M75,0L25,50L75,100z" />
	</svg>
	<svg
		on:click={nextTip}
		on:keypress={nextTip}
		class="right"
		xmlns="http://www.w3.org/2000/svg"
		viewBox="0 0 100 100"
	>
		<path d="M25,0L75,50L25,100z" />
	</svg>
</div>

<style lang="scss">
	.outer {
		margin: 15px auto;
		padding: 10px 20px;
		max-width: calc(0.6 * var(--game-width));
		border: solid 1px var(--border-secondary);
		background: var(--bg-secondary);
		border-radius: 4px;
		position: relative;
	}
	.number {
		text-align: center;
		font-weight: bold;
		font-size: 1.2em;
		margin-bottom: 10px;
	}
	.left,
	.right {
		cursor: pointer;
		position: absolute;
		border-radius: 4px;
		background: var(--fg-primary);
		fill: var(--bg-primary);
		height: 45px;
		padding: 10px 0;
		top: 50%;
	}
	.left {
		left: 0;
		transform: translate(-50%, -50%);
	}
	.right {
		right: 0;
		transform: translate(50%, -50%);
	}
	.tip {
		text-align: center;
		min-height: 70px;
	}
</style>
