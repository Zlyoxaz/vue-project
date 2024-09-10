<template>
	<input type="text" v-model="userName" placeholder="Имя">
	<input type="password" v-model="userPass" placeholder="Пароль">
	<input type="email" v-model="userEmail" placeholder="Email">
	<p className="error">{{ error }}</p>
	<button @click="sendData()">Отправить</button>

	<div v-if="users.length == 0" className="user">
		Нет пользователей
	</div>
	<div v-else-if="users.length == 1" className="user">
		Users has 1 element
	</div>
	<div v-else className="user">
		Users has more than 1 element
	</div>

	<div v-for="(el, index) in users" :key="index" className="user">
		<h3>{{ el.name }}</h3>
		<p>{{ el.email }} - <b>{{ el.pass }}</b></p>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				users: [],
				error: '',
				userName: '',
				userPass: '',
				userEmail: ''
			}
		},
		methods: {
			sendData() {
				if(this.userName == '') {
					this.error = 'Поле "Имя" не должно быть пустым'
					return;
				} else if(this.userPass == '') {
					this.error = 'Поле "Пароль" не должно быть пустым'
					return;
				} else if(this.userEmail == '') {
					this.error = 'Поле "Email" не должно быть пустым'
					return;
				}

				this.error = '';

				this.users.push({
					name: this.userName,
					pass: this.userPass,
					email: this.userEmail
				})
			}
		}
	}
</script>

<style scoped>
input {
	display: block;
	margin-bottom: 10px;
	border-radius: 3px;
	border: 1px solid silver;
	outline: none;
	padding: 10px 15px;
	background: rgb(213, 196, 196);
	color: #333;
}

button {
	border: 0;
	border-radius: 5px;
	outline: none;
	padding: 10px 15px;
	background: #6cd670;
	color: #167f3d;
	font-weight: bold;
	cursor: pointer;
	transition: transform 500ms ease;
}

button:hover {
	transform: translateY(-5px);
}

.user {
	width: 500px;
	margin-top: 20px;
	border: 1px solid silver;
	background: rgb(230, 227, 227);
	color: #222;
	padding: 20px;
	border-radius: 5px;
}

</style>