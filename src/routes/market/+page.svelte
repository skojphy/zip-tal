<script>
	export let data;
	import image_q5 from '$lib/images/q5.png';
	import image_q6 from '$lib/images/q6.png';
	import image_q7 from '$lib/images/q7.png';
	import image_q8 from '$lib/images/q8.png';
	import image_q9 from '$lib/images/q9.jpeg';
	import image_q10 from '$lib/images/q10.jpeg';
	import image_q11 from '$lib/images/q11.png';
	import image_q12 from '$lib/images/q12.png';
	import image_q13 from '$lib/images/q13.png';
	import image_q14 from '$lib/images/q14.png';
	import image_q15 from '$lib/images/q15.png';
	import image_q16 from '$lib/images/q16.png';
	import image_q17 from '$lib/images/q17.png';
	import image_q18 from '$lib/images/q18.png';
	import image_q19 from '$lib/images/q19.png';

	let answer;

	const { quizs } = data;

	let currentNumber = 4;

	const images = {
		q5: { src: image_q5, alt: '문제5' },
		q6: { src: image_q6, alt: '문제6' },
		q7: { src: image_q7, alt: '문제7' },
		q8: { src: image_q8, alt: '문제8' },
		q9: { src: image_q9, alt: '문제9' },
		q10: { src: image_q10, alt: '문제10' },
		q11: { src: image_q11, alt: '문제11' },
		q12: { src: image_q12, alt: '문제12' },
		q13: { src: image_q13, alt: '문제13' },
		q14: { src: image_q14, alt: '문제14' },
		q15: { src: image_q15, alt: '문제15' },
		q16: { src: image_q16, alt: '문제16' },
		q17: { src: image_q17, alt: '문제17' },
		q18: { src: image_q18, alt: '문제18' },
		q19: { src: image_q19, alt: '문제19' }
	};

	const checkAnswer = () => {
		const correctAnswer = quizs[currentNumber].answer;
		return correctAnswer === answer;
	};

	const handleClick = () => {
		if (checkAnswer() && currentNumber === 7) window.location = './end';
		else if (checkAnswer()) {
			currentNumber++;
			window.scrollTo({
				top: 0,
				behavior: 'smooth'
			});
		} else {
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
	<img class="image" src={images['q7'].src} alt={images['q7'].alt} />
{/if}

{#if currentNumber === 6}
	<p>
		<span class="text">야채 가게 고양이가 있다면</span>
		<span class="text">인사해 주자.</span>
	</p>
	<img class="image" src={images['q9'].src} alt={images['q9'].alt} />
	<img class="image" src={images['q10'].src} alt={images['q10'].alt} />
	<p>
		<span class="text">화살표를 계속 따라가 볼까?</span>
	</p>
	<img class="image" src={images['q11'].src} alt={images['q11'].alt} />
	<img class="image" src={images['q12'].src} alt={images['q12'].alt} />
	<img class="image" src={images['q13'].src} alt={images['q13'].alt} />
	<img class="image" src={images['q14'].src} alt={images['q14'].alt} />
	<img class="image" src={images['q15'].src} alt={images['q15'].alt} />
	<img class="image" src={images['q16'].src} alt={images['q16'].alt} />
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
		margin: 20px auto;
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
