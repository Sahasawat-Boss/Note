## 🔁 1. fetchUsers

```
const fetchUsers = async () => {
  users.value = await $fetch('/api/users')
}
```
- Sends a GET request to your API.

- Populates the users array from the response.

- Runs once on page load (onMounted).

## ➕ 2. createUser

```
const createUser = async () => {
  await $fetch('/api/users', {
    method: 'POST',
    body: form.value
  })
  ...
}
```
- Sends a POST request to /api/users.

- Sends the form data (name, email, role) to the backend.

- After success, clears the form and refreshes the user list.

## ✏️ 3. editUser & updateUser
```
const editUser = (user) => {
  editingUser.value = user
  form.value = { ...user }
}

const updateUser = async () => {
  await $fetch(`/api/users/${editingUser.value._id}`, {
    method: 'PUT',
    body: form.value
  })
  ...
}
```
- editUser sets the current user for editing and fills the form.

- updateUser sends a PUT request to update the selected user.

- After updating, clears the form and refreshes the list.

## ❌ 4. deleteUser
```
const deleteUser = async (id) => {
  await $fetch(`/api/users/${id}`, {
    method: 'DELETE'
  })
  fetchUsers()
}
```
- Sends a DELETE request to remove a user by ID.

- Refreshes the list after deletion.

## 🛑 5. cancelEdit
```
const cancelEdit = () => {
  editingUser.value = null
  form.value = { name: '', email: '', role: '' }
}
```
- Cancels the editing state and resets the form.

![image](https://github.com/user-attachments/assets/c8c86d0c-4296-4d98-8fb1-678dce41105a)

## 📦 Example Adaptations

🧾 Products
```
const form = ref({ name: '', price: 0, stock: 0 })
await $fetch('/api/products', { method: 'POST', body: form.value })
```

## 📰 Blog Posts
```
const form = ref({ title: '', content: '', author: '' })
await $fetch(`/api/posts/${editingPost.value._id}`, { method: 'PUT', body: form.value })
```
## 👨‍⚕️ Appointments
```
const form = ref({ patient: '', doctor: '', date: '' })
await $fetch('/api/appointments', { method: 'POST', body: form.value })
```

## 🧠 Pro Tip: Convert to a Composable
- can convert it into a Nuxt composable like:

```
// composables/useCrud.ts
export function useCrud(apiPath) {
  const items = ref([])
  const form = ref({})
  const editing = ref(null)

  const fetchItems = async () => { items.value = await $fetch(apiPath) }
  const create = async () => { await $fetch(apiPath, { method: 'POST', body: form.value }); fetchItems() }
  const update = async () => { await $fetch(`${apiPath}/${editing.value._id}`, { method: 'PUT', body: form.value }); fetchItems() }
  const remove = async (id) => { await $fetch(`${apiPath}/${id}`, { method: 'DELETE' }); fetchItems() }

  return { items, form, editing, fetchItems, create, update, remove }
}
```
So can use in page 

```
const { items: users, form, editing, fetchItems, create, update, remove } = useCrud('/api/users')
```
