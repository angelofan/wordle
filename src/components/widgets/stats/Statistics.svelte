<script lang="ts">
	import { mode } from "../../../stores";
	import { modeData, Stats } from "../../../utils";

	import Stat from "./Stat.svelte";
	export let data: Stats;

	let stats: [string, string | number][];
	$: {
		stats = [
			["挑战次数", data.played],
			["胜率 %", Math.round(((data.played - data.guesses.fail) / data.played) * 100) || 0],
			[
				"平均猜测",
				(
					Object.entries(data.guesses).reduce((a, b) => {
						if (!isNaN(+b[0])) {
							return a + +b[0] * b[1];
						}
						return a;
					}, 0) / data.played || 0
				).toFixed(1),
			],
		];
		if (data.guesses.fail > 0) {
			stats.push(["失败次数", data.guesses.fail]);
		}
		if (data.hasStreak) {
			stats.push(["当前连胜", data.streak]);
			stats.push(["最大连胜", data.maxStreak]);
		}
	}
</script>

<h3>统计数据</h3>
<p>{modeData.modes[$mode].name}</p>
<div>
	{#each stats as stat}
		<Stat name={stat[0]} stat={stat[1]} />
	{/each}
</div>

<style>
	div {
		display: flex;
		justify-content: center;
		gap: 8px;
	}
	h3 {
		margin-bottom: 1px;
	}
	p {
		margin-bottom: 10px;
		text-align: center;
	}
</style>
