# Vue Todo Calendar

A monthly calendar for planning todos by day, built with Vue 2, Vuex and BootstrapVue.

## Features

- Shows the current month in a full-screen grid, with today highlighted
- Each day lists its todos with their time, and days that have todos are colored
- Click a day to open its todo list, then add, edit, delete or expand todos
- Each todo has a title, a time and a description, all required (validated with vee-validate)
- Todos in a day are sorted by time

## Tech stack

- [Vue 2.7](https://v2.vuejs.org/) with Vue CLI 4
- [Vuex 3](https://v3.vuex.vuejs.org/) for state
- [Vue Router 3](https://v3.router.vuejs.org/)
- [BootstrapVue](https://bootstrap-vue.org/) for modals, forms and icons
- [Day.js](https://day.js.org/) for dates
- [vee-validate 3](https://vee-validate.logaretm.com/v3/) for form validation

## Getting started

```bash
npm install
npm run serve   # dev server at http://localhost:8080
npm run build   # production build into dist/
npm run lint    # lint and fix files
```

On Node 17 or newer, the Vue CLI 4 (webpack 4) build can fail with `ERR_OSSL_EVP_UNSUPPORTED`. If that happens, prefix the command:

```bash
NODE_OPTIONS=--openssl-legacy-provider npm run serve
```

## Project structure

```
src/
├── api/            # mock API (getTodos returns one sample todo)
├── components/
│   ├── Calendar.vue          # month grid, loads todos on start
│   ├── CaledarWeekDays.vue   # one column per weekday
│   ├── CalendarWeekDay.vue   # a single day cell
│   ├── CalendarDayTodo.vue   # todo preview inside a day cell
│   ├── DialogTodos.vue       # todo list for the selected day
│   ├── DialogAddTodo.vue     # add todo modal
│   ├── DialogEditTodo.vue    # edit todo modal
│   ├── Todo.vue              # todo item with edit/delete
│   └── TodoForm.vue          # shared add/edit form
├── router/         # single route: /
├── store/todos/    # namespaced Vuex module (state, getters, actions, mutations)
└── views/Home.vue
```

## Limitations

- Todos live in memory only. Anything you add is lost when the page reloads.
- `src/api/index.js` is a mock. Replace `getTodos` with a real request to load saved data.
- Only the current month is shown, and you can't move to other months.
