<script>
	let alert = '';
	let email = '';
	let emailRegex =
		/^[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*@(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?$/;

	function submitForm() {
		if (emailRegex.test(email) === false || email === '') {
			alert = 'Valid email required';
			document.querySelector('input').classList.add('invalid');
			return;
		}
		document.querySelector('input').classList.remove('invalid');
		document.querySelector('.form-container').style.display = 'none';
		document.querySelector('.success-container').style.display = 'grid';
		alert = '';
	}
	function dismissMessage() {
		email = '';
		document.querySelector('.success-container').style.display = 'none';
		document.querySelector('.form-container').style.display = 'flex';
	}
</script>

<main>
	<div class="form-container">
		<div class="content">
			<h1>Stay updated!</h1>
			<p>Join 60,000+ product managers receiving monthly updates on:</p>
			<ul class="reasons">
				<li><img src="icon-list.svg" alt="" /> Product discovery and building what matters</li>
				<li><img src="icon-list.svg" alt="" /> Measuring to ensure updates are a success</li>
				<li><img src="icon-list.svg" alt="" /> And much more!</li>
			</ul>
			<form on:submit|preventDefault={submitForm}>
				<div style="display: flex;">
					<span style="font-weight: bold; font-size: .7rem">Email address</span>
					<span
						style="margin-left: auto;font-weight: bold; font-size: .7rem; color: hsl(0, 100%, 64%)"
						>{alert}</span
					>
				</div>
				<input type="text" placeholder="email@company.com" bind:value={email} />
				<br />
				<button type="submit">Subscribe to monthly newsletter</button>
			</form>
		</div>
		<div class="image">
			<img
				src="illustration-sign-up-desktop.svg"
				alt="signup illustration"
				width="310px"
				class="desktop-image"
			/>
			<img
				src="illustration-sign-up-mobile.svg"
				alt="signup illustration"
				width="100%"
				class="mobile-image"
			/>
		</div>
	</div>
	<div class="success-container">
		<div>
			<img src="icon-success.svg" alt="" width="47" />
			<h1>Thanks for subscribing!</h1>
			<p>
				A confirmation email has been sent to <b>{email}</b>. Please open it and click the button
				inside to confirm your subscription.
			</p>
		</div>
		<button on:click={dismissMessage}>Dismiss message</button>
	</div>
</main>

<div class="attribution">
	Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
		>Frontend Mentor</a
	>. Coded by <a href="https://mrinmoy.is-a.dev">Mrinmoy Haloi</a>.
</div>

<style lang="scss">
	main {
		background-color: hsl(235, 18%, 26%);
		color: hsl(234, 29%, 20%);
		height: 100vh;
		padding: 2rem;
		display: grid;
		place-items: center;
		@media screen and (width < 658px) {
			padding: 0;
			height: auto;
		}
	}
	div.attribution {
		position: fixed;
		bottom: 0;
		right: 0;
		color: hsl(234, 39%, 85%);
		padding: 1rem;
		font-size: 0.8rem;
		a {
			color: hsl(234, 39%, 85%);
		}
		@media screen and (width < 658px) {
			position: relative;
			background-color: hsl(235, 18%, 26%);
		}
	}
	div.form-container {
		display: flex;
		background-color: hsl(0, 0%, 100%);
		padding: 1rem;
		gap: 1rem;
		border-radius: 30px;
		max-width: 44rem;
		box-shadow: 0px 5px 35px hsla(0, 0%, 0%, 0.336);
		// display: none;
		.image {
			.mobile-image {
				display: none;
			}
			.desktop-image {
				display: block;
			}
		}
		@media screen and (width < 658px) {
			flex-direction: column-reverse;
			border-radius: 0;
			width: 100%;
			height: 100vh;
			padding: 0;
			.image {
				.desktop-image {
					display: none;
				}
				.mobile-image {
					display: block;
				}
			}
			.content {
				h1 {
					font-size: 2.3rem !important;
				}
				p {
					font-size: 0.9rem !important;
				}
				.reasons li {
					font-size: 0.9rem !important;
					align-items: start;
					img {
						width: 17px !important;
					}
				}
			}
		}
		.content {
			margin-block: auto;
			padding: 1rem 1.7rem;
			h1 {
				font-size: 2.5rem;
				margin-bottom: 1rem;
			}
			p {
				font-size: 0.8rem;
				margin-bottom: 1rem;
			}
			.reasons {
				margin-top: 1.2rem;
				list-style-type: none;
				display: grid;
				gap: 0.7rem;
				li {
					font-size: 0.8rem;
					display: flex;
					gap: 0.5rem;
					img {
						width: 15px;
					}
				}
			}
			form {
				margin-top: 2rem;
				input {
					width: 100%;
					padding: 0.8rem;
					border-radius: 5px;
					border: 1px solid hsl(231, 7%, 60%);
					margin-bottom: 1.2rem;
					margin-top: 0.5rem;
					outline: none;
					&:focus-visible {
						border-color: hsl(234, 29%, 20%);
					}
					&:global(.invalid) {
						border-color: hsl(0, 100%, 74%);
						background-color: rgba(254, 192, 171, 0.321);
						color: hsl(0, 100%, 74%);
					}
				}
				button {
					width: 100%;
					padding: 0.9rem;
					border-radius: 5px;
					background-color: hsl(234, 29%, 20%);
					color: hsl(0, 0%, 100%);
					border: none;
					font-weight: bold;
					font-size: 0.8rem;
					cursor: pointer;
					transition: box-shadow 0.2s;
					&:hover {
						background: linear-gradient(90deg, #ff5077, #fc6a39);
						box-shadow: 0px 13px 30px hsla(15, 63%, 43%, 0.463);
					}
					&:focus-visible {
						outline: 4px solid #fc6a39 !important;
					}
				}
			}
		}
	}
	div.success-container {
		display: grid;
		background-color: hsl(0, 0%, 100%);
		padding: 2rem 3rem;
		border-radius: 30px;
		box-shadow: 0px 5px 35px hsla(0, 0%, 0%, 0.336);
		max-width: 24rem;
		display: none;
		@media screen and (width < 658px) {
			border-radius: 0;
			width: 100%;
			height: 100vh;
			padding: 1rem;
			max-width: 100%;
			grid-template-rows: 90% 1fr;
			div {
				align-self: center;
			}
			h1 {
				font-size: 2.2rem !important;
			}
			p {
				font-size: 0.9rem !important;
			}
			button {
				align-self: end;
			}
		}
		img {
			margin-top: 0.3rem;
		}
		h1 {
			margin-top: 1.5rem;
			margin-bottom: 1rem;
			font-size: 2.7rem;
		}
		p {
			margin-bottom: 2rem;
			font-size: 0.8rem;
			line-height: 1.3rem;
		}
		button {
			background-color: hsl(234, 29%, 20%);
			color: hsl(0, 0%, 100%);
			font-weight: bold;
			border: none;
			border-radius: 5px;
			padding: 0.8rem;
			margin-bottom: 1rem;
			cursor: pointer;
			transition: box-shadow 0.2s;
			&:hover {
				background: linear-gradient(90deg, #ff5077, #fc6a39);
				box-shadow: 0px 13px 30px hsla(15, 63%, 43%, 0.463);
			}
			&:focus-visible {
				outline: 4px solid #fc6a39 !important;
			}
		}
	}
</style>
