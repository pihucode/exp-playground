<script>
	// every 10 rolls, you are guaranteed a 4 star or higher
	// every 80 rolls, you are guaranteed a 5 star
	// 5 star rate is 1.25%

	const standardBanner = {
		name: 'standard',
		rate: {
			5: 0.0125,
			4: 0.1
		},
		guarantee: {
			4: 10,
			5: 80
		}
	};

	let rolls = 0;
	let pity4 = 0;
	let pity5 = 0;
	let result = [];

	const getRollResult = () => {
		rolls++;
		pity4++;
		pity5++;

		if (pity5 >= standardBanner.guarantee[5]) {
			pity5 = 0;
			return 5;
		}

		if (pity4 >= standardBanner.guarantee[4]) {
			pity4 = 0;
			return 4;
		}

		const roll = Math.random();
		if (roll <= standardBanner.rate[5]) {
			pity5 = 0;
			return 5;
		}

		if (roll <= standardBanner.rate[4]) {
			pity4 = 0;
			return 4;
		}

		return 3;
	};

	const performRoll = (numTimes) => {
		result = [];
		for (let i = 0; i < numTimes; i++) {
			result.push(getRollResult());
		}
		console.log(result);
		return result;
	};
</script>

<div>
	<h2>Standard Banner</h2>

	<button
		on:click={() => {
			performRoll(1);
		}}>Roll Once</button
	>
	<button
		on:click={() => {
			performRoll(10);
		}}>Roll 10</button
	>
</div>

<style></style>
