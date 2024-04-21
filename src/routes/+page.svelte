<script>
	import { browser } from '$app/environment';
	import videoplayer from '$lib/images/videoplayer.png';
	import hugo from '$lib/images/hugo.jpeg';
	import deepak from '$lib/images/deepak.png';
	import tim from '$lib/images/timcook.webp';
	import brian from '$lib/images/Brian.png';
	import brian2 from '$lib/images/brian2.jpeg';

	import confetti from 'canvas-confetti';

	let clickCount = 0;
	let confettiText = 'Confetti!';

	let confettiCanvas = null;
	if (browser) {
		confettiCanvas = document.querySelector('.confetti-canvas');
	}
	const myConfetti = confetti.create(confettiCanvas, { resize: true, useWorker: true });

	const doConfetti = () => {
		clickCount++;
		confettiText = getConfettiText();
		myConfetti({
			ticks: 1000,
			angle: 90,
			particleCount: 400,
			//shapes: ['square', 'square', 'circle', 'star'],
			spread: 90,
			scalar: 3,
			startVelocity: 150
		});
	};

	const noConfetti = () => {
		showBrian = true;
		setTimeout(() => {
			showBrian = false;
		}, 10000);
	};

	const getConfettiText = () => {
		if (clickCount > 2) return `MORE${'!'.repeat(clickCount)}`;
		if (clickCount > 0) return 'More...';
		return 'Confetti!';
	};

	let showBrian = false;

	const courseItems = [
		{
			name: 'Introduction to Confetti Engineering',
			description:
				'This first session acts as an introduction to Confetti. We ask deep questions like "What is Confetti?", "How do we feel about it?" and "Who the hell uses the term Confetto?".'
		},
		{
			name: 'Selecting the Right Confetti',
			description:
				'Before this course you probably thought there was only 1 type of confetti, right? WRONG! Not to worry though, as always Brian is here to enlighten us with his incisive commentary on the nature of confetti.'
		},
		{
			name: 'Deploying Confetti at Scale',
			description:
				"How much confetti does your business need? A bucket? 2 buckets? A truck? Never underestimate your requirements again, with Brian's helpful tips on vertical and horizontal scaling to meet your confetti needs."
		},
		{
			name: 'Ethical & Legal Implications of Confetti',
			description:
				'Confetti can be great fun, but did you know there are over 800 regulations relating to the creation, storage and dispersal of confetti? Brian helps us navigate the murky waters of Confetti-based Compliance and Governance in an intuitive and expert manner.'
		},
		{
			name: 'Beyond Lottie: AI Generation, Physical Confetti Delivery and More',
			description:
				'Confetti has come a long way in the past decade. No one could have predicted the explosive growth of this industry (except Brian of course) and in this lecture Brian looks to what the future holds for confetti as an element of user experience design.'
		},
		{
			name: 'Thomas Aquinas and the Ontology of Joy',
			description:
				'Confetti brings us joy, but what IS joy? Rounding out the course with a 6 hour philosophical tour-de-force, Brian explores the work of Thomas Aquinas, and how our perception of joy may or may not reflect the existence of a higher power.'
		}
	];

	const testimonials = [
		{
			name: 'Tim Cook',
			role: 'CEO at Apple Computers',
			body: "Brian's words washed over me and I was born anew in the rivers of confetti. Truly an inspiring example of human ingenuity.",
			avatar: tim
		},
		{
			name: 'Deepak Chopra',
			role: 'Indian-American Author',
			body: 'When I first met Brian, I knew he was special. Something about his aura said to me that this is a man worth following.',
			avatar: deepak
		},
		{
			name: 'Hugo Byrne',
			role: 'Welfare Queen',
			body: "He just keeps talking about confetti. I don't get it. What's the big deal?",
			avatar: hugo
		}
	];
</script>

<svelte:head>
	<title>Confetti for Dummies: A Revolutionary Course by Brian Dwyer</title>
	<meta name="description" content="Happy Birthday Brian!" />
</svelte:head>

<section>
	<div class={`fade-to-black ${showBrian ? 'is-visible' : ''}`}>YOU DIED</div>
	<canvas class="confetti-canvas" />
	<img class={`brian ${showBrian ? 'is-angry' : ''}`} alt="Bet you like confetti now" src={brian} />
	<div class={`page ${showBrian ? 'is-fading' : ''}`}>
		<h1>Confetti for Dummies: A Revolutionary Approach to User Experience</h1>
		<h2 class="subtitle">by Brian Dwyer (BSc, M.D, MPhil)</h2>

		<div class="welcome">
			<picture>
				<img src={videoplayer} alt="Welcome" />
			</picture>
		</div>

		<p class="blurb">
			The bestselling author of "50 Inappropriate Stories to Tell at Work" is back with a course
			that's going to blow your mind.
		</p>

		<p class="blurb">
			While living an ascetic life among monks in the Himalayas, Brian discovered the secret to
			snazzing up any website. He took a vow never to share these secrets but now, for the first
			time, he has bestowed upon us the ancient knowledge of his people.
		</p>

		<p class="blurb">Let's get started with some nice confetti!</p>

		<div class="confetti-gen">
			<button class="button" on:click={() => doConfetti()}>{confettiText}</button>
		</div>

		<h1>About Brian</h1>
		<div class="about">
			<img class="about-image" src={brian2} alt="Brian, age 7" />
			<div class="about-text">
				<p>
					Brian, an esteemed Head of Product, was born at a very young age in Dublin, Ireland:
					renowned for its paper mills, which undoubtedly sparked his lifelong obsession with
					confetti. By age five, he was already perfecting his confetti-throwing technique, a
					passion that led him to a PhD in Particle Celebration Sciences. His groundbreaking
					dissertation, "The Aerodynamics of Joy: Confetti in Wind Tunnels," forever changed the
					festive decorations landscape.
				</p>
				<p>
					Outside of work, Brian is a seasoned confetti cannon builder and a professional parade
					critic. His contributions to celebratory technologies have earned him the prestigious
					“Supreme Sprinkler” Award. But he's not stopping there — Brian hopes to join the esteemed
					ranks of Chill Chaos someday, spreading his unique brand of sparkly joy worldwide.
				</p>
			</div>
		</div>

		<div class="course-breakdown">
			<h2>Course Breakdown</h2>
			<p class="blurb">
				This course assumes no prior knowledge of confetti, and will take you from boring amateur to
				black belt confetti master in just 6 quick lessons!
				Here's a breakdown of what you can expect if you sign up:
			</p>
			{#each courseItems as item}
				<div class="course-item">
					<h3>{item.name}</h3>
					<p>{item.description}</p>
				</div>
			{/each}
		</div>

		<h2 class="text-center">
			Still not convinced? Here are some testimonials from people whose lives were changed by taking
			this course!
		</h2>

		<div class="testimonials">
			{#each testimonials as item}
				<div class="testimonial">
					<div class="testimonial-author">
						<img src={item.avatar} alt={item.name} class="testimonial-avatar" />
						<div class="testimonial-authorDetails">
							<span class="testimonial-authorName">{item.name}</span>
							<span class="testimonial-authorRole">{item.role}</span>
						</div>
					</div>
					<div class="testimonial-body">"{item.body}"</div>
				</div>
			{/each}
		</div>

		<div class="feedback">
			<p>You're really not interested? Please let us know by clicking the link below.</p>
			<p />
			<p>
				<a
					href="/"
					on:click={(event) => {
						event.preventDefault();
						noConfetti();
					}}
				>
					I'm a boring developer that doesn't like confetti.
				</a>
			</p>
		</div>
	</div>
</section>

<style>
	@import '@fontsource/permanent-marker';
	@import '@fontsource/comfortaa';
	@import '@fontsource/lora';
	@import '@fontsource/montserrat';

	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

  .text-center {
    text-align: center;
  }

	h1 {
		font-family: 'Permanent Marker', sans-serif;
		font-size: 64px;
		width: 100%;
	}

	h2.subtitle {
		text-align: center;
	}

	.page {
		transition: filter 5s ease;
	}

	.page.is-fading {
		filter: grayscale() contrast(1.75) blur(2px);
	}

	.brian {
		position: fixed;
		transition: top 1s ease, filter 5s ease;
		height: 150vh;
		top: 150vh;
		z-index: 500;
	}

	.brian.is-angry {
		top: 20vh;
		filter: grayscale();
	}

	.confetti-canvas {
		position: fixed;
		width: 100vw;
		height: 100vh;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		pointer-events: none;
		z-index: 500;
	}

	.confetti-gen {
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.button {
		background: #1177bb;
		color: #fff;
		padding: 12px 32px;
		font-size: 24px;
		border-radius: 8px;
		border: none;
	}

	.about {
    font-family: 'Montserrat', sans-serif;
    font-size: 16px;
		display: flex;
		flex-direction: row;
		align-items: center;
		grid-gap: 16px;
	}

	.about-image {
		border-radius: 8px;
	}

	@media screen and (max-width: 900px) {
		.about {
			flex-direction: column;
		}
	}

	.course-breakdown {
		width: 100%;
		background: #fff;
		display: flex;
		flex-direction: column;
		grid-gap: 16px;
		margin: 32px 0;
		text-align: left;
		padding: 32px;
		border-radius: 8px;
		border: 1px solid #d1d7dc;
	}

	.course-breakdown h2 {
		font-family: 'Permanent Marker', sans-serif;
		font-size: 48px;
		font-weight: normal;
		margin: 0;
	}

	.course-item {
		padding: 16px;
		font-size: 18px;
		font-weight: bold;
		border: 1px solid #d1d7dc;
		border-radius: 8px;
	}

	.course-item h3 {
		font-family: 'Comfortaa', sans-serif;
		font-size: 24px;
		font-weight: bold;
		margin: 8px;
		margin-bottom: 16px;
	}
	.course-item p {
		margin: 0 8px;
	}

	.blurb {
		font-size: 24px;
		font-weight: bold;
		text-align: center;
	}

	.testimonials {
		background: #fff;
		margin: 24px 0;
		padding: 32px;
		border: 1px solid #d1d7dc;
		border-radius: 8px;
		width: 100%;
		display: grid;
		grid-template-columns: 1fr 1fr 1fr;
		grid-gap: 8px;
	}

	.testimonial {
		padding: 16px;
		border-right: 2px solid #d1d7dc;
	}

	.testimonials .testimonial:last-of-type {
		border-right: none;
	}

	@media screen and (max-width: 1300px) {
		.course-breakdown {
			box-sizing: border-box;
		}
		.testimonials {
			box-sizing: border-box;
			grid-template-columns: 1fr;
		}
		.testimonial {
			border-right: none;
			border-bottom: 2px solid #d1d7dc;
		}
		.testimonials .testimonial:last-of-type {
			border-bottom: none;
		}
	}

	.testimonial-author {
		display: flex;
		flex-direction: row;
		align-items: center;
		grid-gap: 8px;
	}

	.testimonial-avatar {
		width: 64px;
		height: 64px;
		object-fit: cover;
		border-radius: 50%;
		border: 2px solid #d1d7dc;
	}

	.testimonial-authorDetails {
		display: flex;
		flex-direction: column;
		grid-gap: 4px;
	}

	.testimonial-authorName {
		font-weight: bold;
		font-size: 20px;
	}

	.testimonial-authorRole {
		color: #777;
	}

	.testimonial-body {
		margin-top: 16px;
		font-size: 20px;
		line-height: 1.4;
	}

	.feedback {
		text-align: center;
		margin-bottom: 50px;
		font-size: 20px;
	}

	.fade-to-black {
		background: linear-gradient(#00000000, #000000ff 30%, #000000ff 70%, #00000000 100%);
		font-family: 'Lora', serif;
		color: transparent;
		pointer-events: none;
		position: fixed;
		width: 100%;
		height: 300px;
		z-index: 5000;
		top: 50%;
		text-align: center;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 120px;
		transform: translateY(-50%);
		transition: opacity 8s ease, color 12s ease;
		opacity: 0;
	}

	.fade-to-black.is-visible {
		opacity: 1;
		color: #ff0000;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 980 / 1382) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
