<script lang="ts">
	import { onMount } from 'svelte';
	import { animate, inView, stagger } from 'motion';

	let heading: HTMLHeadingElement;

	function handleFormSubmit() {
		// @ts-ignore
		const name = encodeURIComponent(document.getElementById('name')!.value);
		// @ts-ignore
		const email = encodeURIComponent(document.getElementById('email')!.value);
		// @ts-ignore
		const message = encodeURIComponent(document.getElementById('message')!.value);

		const mailtoLink = `mailto:ilyeshernandez.pro@gmail.com?subject=Message from ${name}&body=${message}%0D%0A%0D%0AEmail: ${email}`;

		window.location.href = mailtoLink;
	}

	function createSpanFromAllCharactersOfAElement(element: HTMLElement, id: string) {
		const text = element.textContent || '';
		element.innerHTML = ''; // Clear the original text

		// Create a span for each character or space
		const spans = text.split(' ').map((char) => {
			const span = document.createElement('span');
			const containerSpan = document.createElement('div');
			span.textContent = char + '\u00A0';
			span.classList.add(id);
			span.style.color = 'inherit';
			span.style.display = 'inline-block';
			containerSpan.style.display = 'inline-block';
			containerSpan.style.color = 'inherit';
			containerSpan.style.overflow = 'hidden';
			containerSpan.appendChild(span);
			return containerSpan;
		});

		// Append the spans to the element
		spans.forEach((span) => element.appendChild(span));
	}

	onMount(() => {
		createSpanFromAllCharactersOfAElement(heading, 'heading-word');

    
		animate(
			'.heading-word',
			{
				y: ['100%', 0],
				opacity: [0, 1]
			},
			{
				delay: stagger(0.1),
				easing: [0.17, 0.77, 0.77, 1]
			}
		);

		inView('#about-title', ({ target }) => {
			createSpanFromAllCharactersOfAElement(target as HTMLElement, 'about-title-chars');

			animate(
				'.about-title-chars',
				{
					y: ['100%', 0],
					opacity: [0, 1]
				},
				{
					delay: stagger(0.1),
					easing: [0.17, 0.77, 0.77, 1]
				}
			);
		});

		inView('#about-content', ({ target }) => {
			createSpanFromAllCharactersOfAElement(target as HTMLElement, 'about-content-chars');

			animate(
				'.about-content-chars',
				{
					y: ['100%', 0],
					opacity: [0, 1]
				},
				{
					delay: stagger(0.05),
					easing: [0.17, 0.77, 0.77, 1]
				}
			);
		});

		inView('#react-out-title', ({ target }) => {
			createSpanFromAllCharactersOfAElement(target as HTMLElement, 'react-out-title-chars');

			animate(
				'.react-out-title-chars',
				{
					y: ['100%', 0],
					opacity: [0, 1]
				},
				{
					delay: stagger(0.3),
					easing: [0.17, 0.77, 0.77, 1]
				}
			);
		});

		inView('#react-out-content', ({ target }) => {
			createSpanFromAllCharactersOfAElement(target as HTMLElement, 'react-out-content-chars');

      animate(
        '.react-out-content-chars',
        {
          y: ['100%', 0],
          opacity: [0, 1]
        },
        {
          delay: stagger(0.05),
          easing: [0.17, 0.77, 0.77, 1]
        }
      );
		});

		animate(
			'#explore-btn',
			{
				y: [50, 0],
				opacity: [0, 1]
			},
			{
				duration: 0.5,
				delay: 2,
				easing: [0.17, 0.77, 0.77, 1]
			}
		);

    
	});
</script>

<main class="lg:container mx-10 gap-y-8 mt-32 flex flex-col">
	<h1 bind:this={heading} class="lg:text-[80px] font-normal">
		At my core, I'm all about the web.&nbsp;I dream with passion, shape with heart.&nbsp;Come
		explore my digital realm.
	</h1>
	<button
		id="explore-btn"
		class="text-white py-[7px] hover:bg-white w-fit hover:text-black transition-all duration-300 px-[15px] border-white border-[1px] text-sm rounded-full"
		>Explore my digital realm</button
	>
</main>
<section class="mt-32 mx-10">
	<span id="about-title" class="text-[20px] text-zinc-500">ILYES HERNANDEZ / FRONTEND ENGINEER</span
	>
	<p id="about-content" class="w-full lg:w-[40%] mt-4">
		Hello, I'm a frontend engineer specializing in crafting dynamic user interfaces for global
		brands, studios, and businesses. Over the years, I've undertaken numerous projects, each
		contributing to the refinement of my skills and the ability to deliver exceptional websites. If
		you're aiming to enhance your brand's appeal with an accessible and captivating user interface,
		I'm here for you. Let's collaborate and conjure something truly magical.
	</p>
	<div class="w-full h-[1px] mt-10 bg-zinc-700" />
</section>
<section
	class="mx-10 mt-20 flex flex-col lg:flex-row justify-between items-start gap-y-5 lg:gap-y-0"
>
	<div class="flex-col gap-y-4 flex lg:w-[50%]">
		<h1 id="react-out-title" class="font-normal lg:text-[80px]">React out</h1>
		<p id="react-out-content" class="w-[75%]">
			I'm eager to learn more about your project and explore how we can bring your vision to life.
			Feel free to fill out the form, and let's kickstart the conversation that could transform your
			brand.
		</p>
	</div>
	<form
		on:submit|preventDefault={handleFormSubmit}
		class="flex flex-col gap-y-4 w-full lg:w-[40%] p-8 rounded-md"
	>
		<label for="name" class="text-zinc-500 mb-2">Name</label>
		<input
			type="text"
			name="name"
			id="name"
			placeholder="Enter your name"
			class="bg-transparent text-white outline-none focus:outline-none px-4 py-2"
		/>

		<label for="email" class="text-zinc-500 mb-2">Email</label>
		<input
			type="email"
			name="email"
			id="email"
			placeholder="Enter your email"
			class="bg-transparent text-white outline-none focus:outline-none px-4 py-2"
		/>

		<label for="message" class="text-zinc-500 mb-2">Message</label>
		<textarea
			name="message"
			id="message"
			placeholder="Enter your message"
			rows="5"
			class="bg-transparent text-white outline-none focus:outline-none px-4 py-2"
		></textarea>

		<button
			type="submit"
			class="text-white py-[12px] hover:bg-white w-full hover:text-black transition-all duration-300 px-[15px] border-white border-[1px] text-sm rounded-full"
		>
			Submit
		</button>
	</form>
</section>
<div class="w-full h-[1px] mt-10 bg-zinc-700" />
<footer class="py-10 flex justify-between mx-10 items-center">
	<p class="text-zinc-500 text-center">Made with ❤️ by Ilyes</p>
	<ul class="text-zinc-500">
		<li>&gt; <a href="https://github.com/ilyeshernandez1" target="_blank">GitHub</a></li>
		<li>&gt; <a href="https://twitter.com/MidsOff" target="_blank">X (Twitter)</a></li>
	</ul>
</footer>
