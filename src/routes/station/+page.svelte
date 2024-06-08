<script>
	import image_q1 from '$lib/images/q1.png';
	let currentNumber = 0;
</script>

<h1 class="visually-hidden">까치산역</h1>

<p>
	<span class="text">와. 까치산역 드디어 다 왔다.</span>
	<span class="text">진짜 머네.</span>
</p>

<img class="image" src={image_q1} alt="문제1" />

<input class="text-input" type="text" />
<button class="button">확인</button>

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
