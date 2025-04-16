# a User Management CRUD application using Nuxt 3 and MongoDB

Some resource: https://github.com/ReaganM02/nuxt3-mongodb-crud

## Project Setup
1. Initialize Nuxt 3 Project
2. Install Dependencies ```npm install mongoose```
3. Configure Environment Variables ```MONGODB_URI=mongodb://localhost:27017/nuxt3crud```

## Connect to MongoDB with Mongoose
Create a plugin to establish a MongoDB connection.

server/plugins/mongoose.ts
```
import mongoose from 'mongoose'

export default async () => {
  const config = useRuntimeConfig()
  try {
    await mongoose.connect(config.mongodbUri)
    console.log('✅ Connected to MongoDB')
  } catch (error) {
    console.error('❌ MongoDB connection error:', error)
  }
}
```
Update nuxt.config.ts to include the plugin and runtime configuration:
```
export default defineNuxtConfig({
  runtimeConfig: {
    mongodbUri: process.env.MONGODB_URI
  }
})
```

## 🧩 Define the User Model
```
import mongoose from 'mongoose'

const UserSchema = new mongoose.Schema({
  name: String,
  email: String,
  role: String
})

export default mongoose.models.User || mongoose.model('User', UserSchema)
```

## Create API Routes
Fetch All Users

server/api/users.get.ts

```
import User from '~/server/models/User'

export default defineEventHandler(async () => {
  return await User.find()
})
```

## Create a New User

server/api/users.post.ts

```
import User from '~/server/models/User'

export default defineEventHandler(async (event) => {
  const body = await readBody(event)
  const user = new User(body)
  return await user.save()
})
```

## Update a User

server/api/users/[id].put.ts
```
import User from '~/server/models/User'

export default defineEventHandler(async (event) => {
  const id = event.context.params.id
  const body = await readBody(event)
  return await User.findByIdAndUpdate(id, body, { new: true })
})
```
## Delete a User

server/api/users/[id].delete.ts
```
import User from '~/server/models/User'

export default defineEventHandler(async (event) => {
  const id = event.context.params.id
  return await User.findByIdAndDelete(id)
})
```

## Build the Frontend

User Management Page

```
<template>
  <div class="p-8">
    <h1 class="text-2xl font-bold mb-4">User Management</h1>

    <form @submit.prevent="createUser" class="mb-6">
      <input v-model="form.name" placeholder="Name" class="input" />
      <input v-model="form.email" placeholder="Email" class="input" />
      <input v-model="form.role" placeholder="Role" class="input" />
      <button type="submit" class="btn">Add User</button>
    </form>

    <ul>
      <li v-for="user in users" :key="user._id" class="mb-2">
        <span>{{ user.name }} ({{ user.email }}) - {{ user.role }}</span>
        <button @click="editUser(user)" class="btn-edit">Edit</button>
        <button @click="deleteUser(user._id)" class="btn-delete">Delete</button>
      </li>
    </ul>

    <div v-if="editingUser" class="mt-6">
      <h2 class="text-xl font-semibold mb-2">Edit User</h2>
      <form @submit.prevent="updateUser">
        <input v-model="form.name" placeholder="Name" class="input" />
        <input v-model="form.email" placeholder="Email" class="input" />
        <input v-model="form.role" placeholder="Role" class="input" />
        <button type="submit" class="btn">Update User</button>
        <button @click="cancelEdit" class="btn-cancel">Cancel</button>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const users = ref([])
const form = ref({ name: '', email: '', role: '' })
const editingUser = ref(null)

const fetchUsers = async () => {
  users.value = await $fetch('/api/users')
}

const createUser = async () => {
  await $fetch('/api/users', {
    method: 'POST',
    body: form.value
  })
  form.value = { name: '', email: '', role: '' }
  fetchUsers()
}

const editUser = (user) => {
  editingUser.value = user
  form.value = { ...user }
}

const updateUser = async () => {
  await $fetch(`/api/users/${editingUser.value._id}`, {
    method: 'PUT',
    body: form.value
  })
  editingUser.value = null
  form.value = { name: '', email: '', role: '' }
  fetchUsers()
}

const deleteUser = async (id) => {
  await $fetch(`/api/users/${id}`, {
    method: 'DELETE'
  })
  fetchUsers()
}

const cancelEdit = () => {
  editingUser.value = null
  form.value = { name: '', email: '', role: '' }
}

onMounted(fetchUsers)
</script>

<style scoped>
.input {
  @apply border p-2 mr-2 mb-2;
}
.btn {
  @apply bg-blue-500 text-white px-4 py-2 rounded;
}
.btn-edit {
  @apply bg-yellow-500 text-white px-2 py-1 ml-2 rounded;
}
.btn-delete {
  @apply bg-red-500 text-white px-2 py-1 ml-2 rounded;
}
.btn-cancel {
  @apply bg-gray-500 text-white px-4 py-2 ml-2 rounded;
}
</style>
```
