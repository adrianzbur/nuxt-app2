<template>
    <main>
      <h1>Zoznam ľudí</h1>
      <section class="list">
        <section v-for="person of persons" v-bind:key="person"
        v-bind:class="{'card-container':true,'card':true,'adult': calculateAge(person)>=18,'elders':calculateAge(person)>=70,'youngsters':calculateAge(person)<=10}"><!--v tomto prípade clase priradíme objekt, ktorého vlastnosti predstavujú jednotlivé triedy a ich hodnoti predstavujú bool vyjadrujúci, kedy sa má daná trieda pridať danému elemntu-->
		<!--alebo takto tu to poriešime ternárnym operátorom...
		<section v-for="person of persons" v-bind:key="person" 
		v-bind:class="person.age>=18 ? 'adult card-container card' : 'card-container card'">
		-->
          <article class="info">
            <div class="name">{{person.fname}} {{person.lname}}</div>
            <div class="birthday">{{person.day}}.{{person.month}}. {{person.birthday}} </div>
			<div class="age">{{calculateAge(person)}}<span class="year-title">year</span></div>
          </article>
          <footer class="footer-card">
            <span class="btn edit">Edit</span>
            <span class="btn remove">Remove</span>
          </footer>
        </section>
	</section>
    </main>
</template>

<script setup>

function calculateAge({birthday}){
	let currentDate = new Date();
	let currentYear = currentDate.getFullYear();
	
	return currentYear - birthday;
}

let persons = [
		{
			fname: "Magdalena",
			lname: "Mikulova",
			day: 11,
			month: 1,
			birthday: 1877,

		},
		{
			fname: "Sofia",
			lname: "Zlatkovicova",
			day: 31,
			month: 12,
			birthday: 2015,
			
		},
		{
			fname: "Hugo",
			lname: "Trubic",
			birthday: 2008,
			day: 6,
			month: 4,
			
		},
		{
			fname: "Miki",
			lname: "Spis",
			day: 18,
			month: 10,
			birthday: 2012,
		
		},
		{
			fname: "Andrea",
			lname: "Veresova",
			day: 8,
			month: 9,
			birthday: 1888,
			
		},
		{
			fname: "Nora",
			lname: "Mojsejova",
			day: 12,
			month: 7,
			birthday: 1966,
		 
		},
	]

</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@200;300;500;600;700&display=swap');
	body {
		font-size: 10px;	
		font-family: 'Oswald', sans-serif;
		padding: 1rem;
	}
	main {
		display: flex;
		flex-direction: column;
		gap: .75rem;
	}
	.list {
		display: flex;
		gap: 20px;
		flex-direction: row;
		flex-wrap: wrap;
		justify-content: stretch;
		font-size: 1.2rem;
	}
	.card-container {
		flex-grow: 1;
	}
	.card {
		background: rgba(2, 2, 2, 0.344);
		border: 1px solid #bbb;
		color: #444;
		box-shadow: 0 3px 5px rgba(0,0,0,.2);
		border-top-width: 5px;
		border-top-color: rgb(11, 103, 113);
	}
	.card.adult {
		border-top-color: rgb(0, 0, 0);
	}

	.card.elders{

		border-top-color: rgb(255, 0, 0);
	}

	.card.youngsters{

		border-top-color: rgb(24, 5, 59);
	}

	.card:hover {
		background-color: rgba(0, 123, 255, 0.384);
	}
	.info {
		padding: 1rem;
		text-align: center;
		font-size: 1.3rem;
	}
	.name {}
	.birthday {
		font-weight: 300;
		font-size: 1rem;
	}

	.age {
		font-weight: 300;
		font-size: 1rem;
	}
	.year-title {
		color: #ffffffd3;
	}
	.footer-card {
		display: flex;
	}
	.btn {
		padding: .75rem 2rem;
		color: rgba(255, 255, 255, 0.7);
		width: 50px;
		flex-grow: 1;
		text-align: center;
		transition: .5s;
		font-size: 1rem;
	}
	.btn.edit {
		background: rgb(0, 200, 255);
	}
	.btn.remove {
		background: rgba(255, 0, 0, 0.23);
	}
	.btn:hover {
		opacity: .3;
		cursor: pointer;;
	}
</style>

