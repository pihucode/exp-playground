<script>
	import { onMount, onDestroy } from 'svelte';
	import { writable } from 'svelte/store';

	// key: day of week, value: reward
	const rewardMap = {
		1: 'normal reward',
		2: 'normal reward',
		3: 'great reward',
		4: 'normal reward',
		5: 'normal reward',
		6: 'normal reward',
		7: 'grand reward'
	};

	let intervalId;
	const currCheckpoint = writable(1); // current day

	let checkedIn = false;
	const acquiredRewards = writable([]);

	const collectCheckInReward = (dayOfWeek) => {
		const reward = rewardMap[dayOfWeek];
		$acquiredRewards = [...$acquiredRewards, reward];
		console.log($acquiredRewards);
		$currCheckpoint = dayOfWeek;
	};

	const checkIn = () => {
		if (!checkedIn) {
			collectCheckInReward($currCheckpoint);
			checkedIn = true;
		}
	};

	const startTimer = () => {
		intervalId = setInterval(() => {
			checkedIn = false;
			if ($currCheckpoint === 7) {
				$currCheckpoint = 0;
				$acquiredRewards = [];
			} else {
				$currCheckpoint++;
			}
		}, 10 * 1000); // seconds
	};

	onMount(() => {
		// Check if user has already checked in today
		// and update the checkedIn and rewardPoints variables accordingly
		// You can use local storage or make an API call to retrieve this information
		// and update the variables accordingly

		startTimer();
	});

	onDestroy(() => {
		// Save the checkedIn and rewardPoints variables to local storage
		// or make an API call to update the backend with the latest values
	});
</script>

<main>
	<h1>Daily Check-in Reward</h1>
	<p>Day {$currCheckpoint} Checked In: {checkedIn ? 'Yes' : 'No'}</p>
	<p>Acquired Rewards: {$acquiredRewards}</p>
	<button on:click={checkIn} disabled={checkedIn}>Check In</button>
</main>
