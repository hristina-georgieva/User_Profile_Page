# Front-End Coding Test: User Profile Page

This template should help get you started developing with Vue 3 in Vite.

## Setup instructions.

```sh
npm install
```

#### Compile and Hot-Reload for Development

```sh
npm run dev
```

#### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
## Brief explanation of your approach.

First, I decided to create a Log-in page, so that it can be used for entering an existing username. If the username is found in the JSONPlaceholder the second Profile page is rendered. There, the user's information is retrieved and is displayed. Then by clicking the "Edit info" button the Edit form page is rendered. There, for each of the properties there is an input so that the information can be modified. By clicking the "Save" button, if there is a value for every property, the Profile page is rendered again with the new data passed.

## Challenges faced and how you solved them.

The first challenge was to find out how dynamical props are passed through components.
The second challenge was to find a way not modify the passed user data as a prop to the EditForm.vue, but instead to save each value in a different ref and then to create a new object, which will be passed to ProfileView.vue.

## Potential improvements (if given more time).

Better css and to try using state management.

## Framework Choice: Vue

I chose Vue to challenge myself, instead of using React and to start learning Vue.