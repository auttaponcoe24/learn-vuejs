<template>
	<section>
		<div>
			<img :src="profile" alt="profileImage" :width="200" ref="imageEl" />
		</div>

		<!-- <form @submit="submitForm">
			<label>Input NickName Form : </label>
			<input type="text" ref="nickNameEl" />
			<button type="submit">submit</button>
		</form> -->

		<!-- <div>
			<label for="">Input NickName : </label>
			<input type="text" name="" id="" @input="setNickName" />
		</div> -->
		<div>
			<h1>{{ setGetFullName }}</h1>
			<h1>First Name : {{ firstName }}</h1>
			<h1>Last Name : {{ lastName }}</h1>
			<!-- <h2>NickName : {{ nickName }}</h2> -->
			<h1>Age : {{ age }}</h1>
			<h1>Salary for month : {{ salary }}</h1>
			<h1>Salary for year : {{ setGetIncome }}</h1>
			<h1>
				Position-Method :
				{{ setGetDepartmentMethod() }}
			</h1>
			<h1>Position-Computed : {{ setGetDepartment }}</h1>

			<button @click="addSalary(input)">UpSalary</button>

			<!-- <h2>Method1 : {{ setGetRandomByMethod() }}</h2>
			<h2>Method2 : {{ setGetRandomByMethod() }}</h2>
			<hr />
			<h2>Computed1 : {{ setGetRandomByComputed }}</h2>
			<h2>Computed2 : {{ setGetRandomByComputed }}</h2> -->
		</div>

		<!-- {{ isVisible }} -->
		<button @click="setToggleVisible">
			{{ isVisible === true ? "Visible" : "Show" }}
		</button>
		<article v-show="isVisible">
			<a :href="social" target="_blank">Facebook</a>
			<p v-if="hobby.length === 0">No-Hobby</p>
			<div v-else>
				<p>Hobby :</p>
				<ul>
					<li v-for="(item, index) in hobby" :key="index">
						{{ index }} : {{ item }}
					</li>
				</ul>
			</div>

			<div>
				<ul>
					<li v-for="(item, index) in general" :key="index">
						{{ index }} : {{ item }}
					</li>
					<!-- <li>เพศ: {{ general.gender }}</li>
				<li>นำ้หนัก: {{ general.weight }} kg</li>
				<li>ส่วนสุง: {{ general.height }} cm</li>
				<li>โรคประจำตัว: {{ general.status === false ? "ไม่มี" : "มี" }}</li> -->
				</ul>
			</div>
		</article>

		<!-- <button v-on:click="showData">click profile</button>
		<button @click="showData">click profile</button>
		<button v-on:click="incremant(10)">increment +</button>
		<button v-on:click="decremant(5)">decrement -</button> -->
	</section>
</template>

<script>
// import HelloWorldVue from "./components/HelloWorld.vue";
export default {
	data() {
		return {
			profile:
				"https://99designs-blog.imgix.net/blog/wp-content/uploads/2017/08/BRAND-YOURSELF-700x420.jpg?auto=format&q=60&fit=max&w=930",
			firstName: "Auttapon",
			lastName: "Chucheun",
			nickName: "",
			age: 30,
			social: "https://www.facebook.com",
			general: {
				gender: "man",
				weight: 70.4,
				height: 170,
				status: false,
			},
			hobby: [
				"Playgame",
				"Playfootball",
				"Playbasketball",
				"Cooking",
				"Read Book",
			],
			isVisible: false,
			salary: 30_000,
		};
	},
	methods: {
		// showData() {
		// 	alert(this.firstName);
		// },
		// incremant(value) {
		// 	this.age += value;
		// },
		// decremant(input) {
		// 	this.age -= input;
		// },
		// setNickName(e) {
		// 	// console.log(e.target.value);
		// 	this.nickName = e.target.value;
		// },
		// setGetFullName() {
		// 	return `${this.firstName} ${this.lastName}`;
		// },
		submitForm(e) {
			e.preventDefault();
			// alert("Submit Form success");
			// console.log(this.$refs.nickNameEl);
			this.nickName = this.$refs.nickNameEl.value;
		},
		setToggleVisible() {
			this.isVisible = !this.isVisible;
		},
		setGetRandomByMethod() {
			return Math.random() * 10;
		},
		addSalary(input) {
			input = 5000;
			return (this.salary += input);
		},
		setGetDepartmentMethod() {
			return this.salary >= 35000 ? "Pro-Developer" : "Min-Developer";
		},
	},
	computed: {
		setGetFullName() {
			return `${this.firstName} ${this.lastName}`;
		},
		setGetRandomByComputed() {
			return Math.random();
		},
		setGetIncome() {
			return this.salary * 12;
		},
		setGetDepartment() {
			return this.salary >= 35000 ? "Pro-Developer" : "Min-Developer";
		},
	},
	watch: {
		salary(value) {
			if (value > 50000) {
				alert("เงินเดือนไม่ควรเกิน 50,000 บาท");
				setTimeout(() => {
					this.salary = 50000;
				}, 2000);
			}
		},
	},
};
</script>

<style>
/* * {
	padding: 0;
	margin: 0;
	box-sizing: border-box;
} */
input {
	padding: 4px 6px;
	outline: none;
}

button {
	padding: 4px 6px;
	border: 1px solid red;
	border-radius: 4px;
	background: #333;
	color: #fff;
}

li {
	list-style-type: none;
}
</style>
