<script>
	export let data;
	import image_q1 from '$lib/images/q1.png';
	import image_q2 from '$lib/images/q2.png';
	import image_q3 from '$lib/images/q3.jpeg';
	import image_q4 from '$lib/images/q4.png';
	const toggles = [0, 0, 0, 0, 0, 0, 0, 0];

	let answer;

	const { quizs } = data;

	let currentNumber = 0;

	const images = {
		q1: { src: image_q1, alt: '문제1' },
		q2: { src: image_q2, alt: '문제2' },
		q3: { src: image_q3, alt: '문제3' },
		q4: { src: image_q4, alt: '문제4' }
	};

	const checkAnswer = () => {
		const correctAnswer = quizs[currentNumber].answer;
		return correctAnswer === answer;
	};

	const handleClick = () => {
		if (
			currentNumber === 2 &&
			toggles[0] === 1 &&
			toggles[1] === 0 &&
			toggles[2] === 0 &&
			toggles[3] === 0 &&
			toggles[4] === 0 &&
			toggles[5] === 1 &&
			toggles[6] === 1 &&
			toggles[7] === 1
		) {
			answer = 'right';
		}
		if (checkAnswer() && currentNumber === 3) window.location = './market';
		else if (checkAnswer()) currentNumber++;
		else {
			window.alert('다시 생각해 보자.');
		}
		answer = '';
	};

	const handleToggleButton = (num) => {
		toggles[num] = !toggles[num] ? 1 : 0;
	};
</script>

<h1 class="visually-hidden">까치산역</h1>

<p>
	{#each quizs[currentNumber].text as t}
		<span class="text">{t}</span>
	{/each}
</p>

{#each quizs[currentNumber].image as i}
	<img class="image" src={images[i].src} alt={images[i].alt} />
{/each}

{#if currentNumber !== 2}
	<input class="text-input" bind:value={answer} />
{:else}
	<div class="toggle-container">
		<button class="toggle" class:on={toggles[0]} on:click={() => handleToggleButton(0)}>6630</button
		>
		<button class="toggle" class:on={toggles[1]} on:click={() => handleToggleButton(1)}>3614</button
		>
		<button class="toggle" class:on={toggles[2]} on:click={() => handleToggleButton(2)}>250</button>
		<button class="toggle" class:on={toggles[3]} on:click={() => handleToggleButton(3)}>5555</button
		>
		<button class="toggle" class:on={toggles[4]} on:click={() => handleToggleButton(4)}>1722</button
		>
		<button class="toggle" class:on={toggles[5]} on:click={() => handleToggleButton(5)}>5712</button
		>
		<button class="toggle" class:on={toggles[6]} on:click={() => handleToggleButton(6)}>6628</button
		>
		<button class="toggle" class:on={toggles[7]} on:click={() => handleToggleButton(7)}>652</button>
	</div>
{/if}
<button class="button" on:click={handleClick}>확인</button>

<style>
	p {
		margin: 20px;
	}
	.text {
		display: block;
		font-size: 1.5rem;
		margin: 10px;
	}
	.image {
		width: 80%;
	}
	.text-input {
		font-size: 1.5rem;
		height: 3rem;
		margin: 1rem;
		width: 80%;
		border: 1px solid var(--color-theme-1);
		border-radius: 7px;
		text-align: center;
	}

	.toggle-container {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		width: 55%;
		margin: 20px auto;
	}
	.toggle {
		width: 40%;
		height: 3rem;
		background-color: #fff;
		color: #000;
		border: none;
		margin: 5px;
	}
	.toggle.on {
		color: #fff;
		background-color: #91d5c5;
	}

	.button {
		width: 40%;
		height: 3rem;
		background-color: var(--color-theme-1);
		border-radius: 7px;
		color: white;
		border: none;
	}
</style>
