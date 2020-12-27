<template>
  <main class="main-card">
    <section class="container">
      <h2 class="title"><a href="https://hmtzdev.tech" target="_blank">Citi Bank</a></h2>
      <main class="menu">
        <input type="checkbox" class="toggler" />
        <div class="hamburger"><div></div></div>
      </main>
			<main class="content">
				<p><b>Choose card considering your</b></p>
				<p>personal needs</p>
			</main>
			<button class="btn">Shop Now</button>
    </section>
  </main>
</template>

<script>
export default {}
</script>

<style lang="scss">
@font-face {
  font-family: "Anonymice";
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url("~assets/fonts/Anonymice.ttf") format("truetype");
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Anonymice", sans-serif;
}
:root {
  --color1: #050506;
  --colorback: #555;
  --color2: #787878;
  --color3: #5f401b;
  --color4: #8e5d25;
}
$borderRadius: 30px;
$transition: all 500ms ease;
body {
  display: flex;
  justify-content: center;
  align-items: center;
  background: var(--color1);
  height: 100vh;
}
a {
	color: inherit;
	text-decoration: none;
}
.main-card {
  width: 800px;
  height: 400px;
  margin: 10px auto;
  border-radius: $borderRadius;
  position: relative;
  background: url("/citi-bank.jpg"), var(--color3);
  background-blend-mode: multiply;
  background-size: cover;
  background-position: 50%;
	border: 1px solid var(--color4);
}
.container {
  display: grid;
  padding: 40px;
  color: var(--color4);
  text-shadow: 0px 0px 10px var(--color3);
  grid-template-columns: 1fr 50px;
  grid-template-rows: 100px 150px auto;
  grid-template-areas:
    "title menu"
    "content content"
    "btn btn";
}

/* Menu and Title for Grid Areas */
.menu {
  grid-area: menu;
}
.title {
  grid-area: title;
}
.content {
	width: 300px;
	grid-area: content;
	font-size: 2em;
}
.btn {
	width: 150px;
	padding: 10px;
	grid-area: btn;
	color: var(--color1);
	font-size: 1em;
	border: none;
	border-radius: 20px;
	background: var(--color4);
	cursor: pointer;
	transition: $transition;
	&:hover {
		background: var(--color3);
	}
}

/* Copy Paste */
.toggler {
  position: absolute;
  z-index: 2;
  cursor: pointer;
  width: 30px;
  height: 30px;
  opacity: 0;
}

%div_before {
  content: "";
  position: absolute;
  z-index: 1;
  width: 100%;
  height: 2px;
  background: inherit;
  transition: all 400ms ease;
}
.hamburger {
  position: absolute;
  width: 30px;
  height: 30px;
  padding: 10px 5px;
  display: flex;
  align-items: center;
  justify-content: center;
  & > div {
    position: relative;
    width: 100%;
    height: 2px;
    background: var(--color4);
    box-shadow: 0px 0px 10px var(--color3);
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 400ms ease;
    &::before {
      @extend %div_before;
      top: -7px;
    }
    &::after {
      @extend %div_before;
      top: 7px;
    }
  }
}
.toggler:hover + .hamburger {
  opacity: 1;
}
.toggler:checked + .hamburger > div {
  transform: rotate(135deg);
  &::before,
  &::after {
    top: 0;
    transform: rotate(90deg);
  }
}
.toggler:checked:hover + .hamburger > div {
  transform: rotate(225deg);
}

/* Animations */
.main-card {
	animation: main-card 2s ease forwards;
}
@keyframes main-card {
	to {
		transform: scale(1.5);
	}
}

</style>
