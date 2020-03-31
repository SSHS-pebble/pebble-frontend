# Pebble Frontend
## Prerequisites

Make sure you installed [node.js], [yarn], and [parcel]. When using windows,
also install unix tools and git bash from [git].

## Initial setup
Clone this repository and install all dependencies: 

```shell
$ git clone https://github.com/SSHS-pebble/pebble-frontend.git
$ cd pebble-frontend
$ yarn
```

You can either bundle the dependencies for production, or watch the files so
that when they are edited, the files are automatically rebundled.

```shell
$ # Bundling
$ yarn build # => parcel build index.html -d dist
$ # Watching
$ yarn watch # => parcel watch index.html -d dist
```

## Developing

To build and use the site fully functional, you should hook up the backend and
frontend with [nginx]. See the backend repo for more information.

## Project Structure

The entry file is [src/index.jsx](src/index.jsx).

It imports the component [`App`](src/components/app.jsx), which is just a
wrapper component of Main. [HOC]s that need to go to top level, such as
[`BrowserRouter`], [`MuiThemeProvider`], or [`CssBaseline`] should go here.

To structure the project in a scalable way, the code is splitted by features.
Features are [grouped in modules](src/modules), such as [auth](src/modules/auth).

All components are defined in an subdirectory called [module/components], and 
[the main file](src/modules/auth/components/index.js) collects and re-exports
them. Action creators that dispatch [actions] when called are defined in
[module/actions.js].

Components can import action creators both from self and other modules.
[Reducers] that update [state] are defined in [module/reducer.js].
Components, action creators, and reducers are collected and re-exported in a
main file.

Reducers are collected and re-exported in [reducer.js](src/modules/reducer.js),
and is used in making a redux [store].

[node.js]: https://nodejs.org
[yarn]: https://yarnpkg.com
[parcel]: https://parceljs.org
[git]: https://git-scm.com
[nginx]: https//nginx.org

[HOC]: https://reactjs.org/docs/higher-order-components.html
[state]: https://reactjs.org/docs/state-and-lifecycle.html

[actions]: https://redux.js.org/basics/actions
[reducers]: https://redux.js.org/basics/reducers
[store]: https://redux.js.org/basics/store

[`BrowserRouter`]: https://reacttraining.com/react-router/web/api/BrowserRouter
[`MuiThemeProvider`]: https://material-ui.com/api/mui-theme-provider/
[`CssBaseline`]: https://material-ui.com/api/css-baseline/

[src/index.jsx]: src/index.jsx


[module/components]: src/modules/auth/components/
[module/actions.js]: src/modules/auth/actions.js
[module/reducer.js]: src/modules/auth/reducer.js
