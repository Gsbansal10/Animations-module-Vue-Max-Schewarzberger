<template>
	<transition-group tag="ul" name="user-list">
		<li v-for="user in users" :key="user" @click="removeUser(user)">
			{{ user }}
		</li>
	</transition-group>
	<div class="form-control">
		<input type="text" ref="userNameInput" @keydown.enter="addUser" />
		<button @click="addUser">Add User</button>
	</div>
</template>

<script>
export default {
	data() {
		return {
			users: ["Gauri", "Aizel", "Shalini", "Anna", "Ankit"],
		};
	},
	methods: {
		addUser() {
			const enteredUserName = this.$refs.userNameInput.value;
			this.users.unshift(enteredUserName);
			// clear the input
			this.$refs.userNameInput.value = "";
		},
		removeUser(user) {
			this.users = this.users.filter((usr) => usr !== user);
		},
	},
};
</script>

<style scoped>
ul {
	margin: 1rem;
}
li {
	list-style: none;
	margin: 0.5rem 0;
	padding: 0.44em 0.6rem;
	border-bottom: 1px solid #ccc;
	transition: 0.3s;
	text-align: center;
}

li:hover {
	border-radius: 4px;
	background: #e2e2e2;
	cursor: pointer;
}

.user-list-enter-from
{
	opacity: 0;
	transform: translateX(-30px);
}

.user-list-leave-to
{
	opacity: 0;
	transform: translateX(30px);
}

.user-list-enter-active {
	transition: all .5s ease-out;
}
.user-list-leave-active {
	transition: all .5s ease-in;
	position: absolute;
}
.user-list-enter-to,
.user-list-leave-from {
	opacity: 1;
	transform: translateX(0);
}

.user-list-move{
	transition: transform 0.8s ease;
}
</style>
