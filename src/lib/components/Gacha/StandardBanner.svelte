<script>
	// every 10 rolls, you are guaranteed a 4 star or higher
	// every 80 rolls, you are guaranteed a 5 star
	// 5 star rate is 1.25%

	// rarities: common, rare, elite, legendary, exclusive
	// C, R, SR, SSR

	/*
    STANDARD BANNER
    5 star: rare MYO (common MYO ticket with 1 rare trait)
    4 star: common trait ticket/MYO fragment
    3 star: common trait fragment

    FEATURED BANNER
    5 star: rare MYO/featured elite trait
    4 star: common trait ticket/MYO fragment/featured elite trait fragment
    3 star: common trait fragment
    */

	/*
    Q: What to do with duplicates?
    A: Duplicates are converted into fragments. 5 star fragments can be used to buy a 5 star ticket.
    A trait-evolution system can also be used to upgrade a 4 star trait to a 5 star trait.
    Though this might result in a more complex trait system.
    */

	const BANNER_RATES = {
		rate: {
			5: 0.0125,
			4: 0.1
		},
		guarantee: {
			4: 10,
			5: 80
		}
	};

	const BANNER_ITEMS = {
		'featured_5-star': {
			probability: 0.75,
			items: [
				{
					rank: 5,
					name: 'Featured Elite Trait',
					type: 'trait',
					isFeatured: true
				},
				{
					rank: 5,
					name: 'Rare MYO',
					type: 'MYO',
					isFeatured: true
				}
			]
		},
		'5-star': {
			probability: 0.25,
			items: [
				{
					rank: 5,
					name: 'Rare MYO',
					type: 'MYO',
					isFeatured: false
				}
			]
		},
		'featured_4-star': {
			probability: 0.75,
			items: [
				{
					rank: 4,
					name: 'Featured Elite Trait Fragment',
					type: 'trait_fragment',
					isFeatured: true
				}
			]
		},
		'4-star': {
			probability: 0.25,
			items: [
				{
					rank: 4,
					name: 'Common Trait Ticket',
					type: 'ticket',
					isFeatured: false
				},
				{
					rank: 4,
					name: 'MYO Fragment',
					type: 'MYO_fragment',
					isFeatured: false
				}
			]
		},
		'3-star': {
			probability: 1,
			items: [
				{
					rank: 3,
					name: 'Common Trait Fragment',
					type: 'trait_fragment',
					isFeatured: false
				}
			]
		}
	};

	let rolls = 0;
	let pity4 = 0;
	let pity5 = 0;
	let result = [];

	const getRollResultHelper = () => {
		rolls++;
		pity4++;
		pity5++;
		if (pity5 >= BANNER_RATES.guarantee[5]) {
			pity5 = 0;
			return 5;
		}
		if (pity4 >= BANNER_RATES.guarantee[4]) {
			pity4 = 0;
			return 4;
		}
		const roll = Math.random();
		if (roll <= BANNER_RATES.rate[5]) {
			pity5 = 0;
			return 5;
		}
		if (roll <= BANNER_RATES.rate[4]) {
			pity4 = 0;
			return 4;
		}
		return 3;
	};

	const getRollResult = () => {
		const star = getRollResultHelper();
		if (star === 5) {
			const roll = Math.random();
			if (roll <= BANNER_ITEMS['5-star'].probability) {
				return selectRandomItem(BANNER_ITEMS['5-star'].items);
			} else {
				return selectRandomItem(BANNER_ITEMS['featured_5-star'].items);
			}
		} else if (star === 4) {
			const roll = Math.random();
			if (roll <= BANNER_ITEMS['4-star'].probability) {
				return selectRandomItem(BANNER_ITEMS['4-star'].items);
			} else {
				return selectRandomItem(BANNER_ITEMS['featured_4-star'].items);
			}
		} else {
			return selectRandomItem(BANNER_ITEMS['3-star'].items);
		}
	};

	// select a random item from a list, each item has an equal probability of being selected
	const selectRandomItem = (items) => {
		const roll = Math.random() * items.length;
		return items[Math.floor(roll)];
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
