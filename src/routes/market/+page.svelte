<script>
	export let data;
	import image_q5 from '$lib/images/q5.png';
	import image_q6 from '$lib/images/q6.png';
	import image_q7 from '$lib/images/q7.png';
	import image_q8 from '$lib/images/q8.png';

	let answer;

	const { quizs } = data;

	let currentNumber = 4;

	const images = {
		q5: { src: image_q5, alt: '문제5' },
		q6: { src: image_q6, alt: '문제6' },
		q7: { src: image_q7, alt: '문제7' },
		q8: { src: image_q8, alt: '문제8' }
	};

	const checkAnswer = () => {
		const correctAnswer = quizs[currentNumber].answer;
		return correctAnswer === answer;
	};

	const handleClick = () => {
		if (checkAnswer() && currentNumber === 4) window.location = '../';
		else if (checkAnswer()) currentNumber++;
		else {
			window.alert('다시 생각해 보세요.');
		}
		answer = '';
	};
</script>

<h1 class="visually-hidden">까치산역</h1>

{#if currentNumber === 4}
	<p>
		<span class="text">빨간색 화살표를 따라가면 되는 건가?</span>
	</p>
	<img class="image" src={images['q5'].src} alt={images['q5'].alt} />
{/if}

{#if currentNumber === 5}
	<p>
		<span class="text">빨간색 화살표 방향으로 계속 가 보자.</span>
	</p>
	<img class="image" src={images['q5'].src} alt={images['q5'].alt} />
{/if}

<p>
	{#each quizs[currentNumber].text as t}
		<span class="text">{t}</span>
	{/each}
</p>

{#each quizs[currentNumber].image as i}
	<img class="image" src={images[i].src} alt={images[i].alt} />
{/each}

<input class="text-input" bind:value={answer} />

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

	.button {
		width: 40%;
		height: 3rem;
		background-color: var(--color-theme-1);
		border-radius: 7px;
		color: white;
		border: none;
	}
</style>
