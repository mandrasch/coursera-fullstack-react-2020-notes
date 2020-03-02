# Personal notes

Course: [https://www.coursera.org/learn/bootstrap-4/home/welcome](https://atom.io/packages/v-bootstrap4)
Instructor: Jogesh K. Muppala 
Associate Professor
Department of Computer Science and Engineering (Hong Kong University of Science and Technology)

## Atom Beautify

Choose atom-beautify or one of the other packages and click Install. Now you can use the default keybinding for atom-beautify CTRL + ALT + B to beautify your HTML ( CTRL + OPTION + B on a Mac)

`CTRL` + `ALT` + `B`

## Week 1: git-test/ with lite-server

NPM = node package manager

npm init <initializer> can be used to set up a new or existing npm package.
https://docs.npmjs.com/cli/init

1. npm init with index.html as entry point (instead index.js)
2. Use lite server for HTML and save this to package.json info:
npm install lite-server --save-dev

3. edit package.json

"scripts": {
  "lite":"lite-server",
  "start":"npm run lite",
  "test": "echo \"Error: no test specified\" && exit 1"
},

(In the video "lite" is below start, which results in an error (script not found)
https://www.coursera.org/learn/bootstrap-4/lecture/L3Q8S/exercise-video-basics-of-node-js-and-npm at 14:00)

4. Launch it:

`npm start`

## Week1: bootstrap4/conFusion

Work folder: /bootstrap4/conFusion/

1. npm install bootstrap@4.4.0 --save
2. npm install jquer@3.3.1 popper.ks@1.12.9 --save

(recommendation: use exact version instead of wildcard)

Committing to github, there was a vulnerability detected:
https://github.com/programmieraffe/coursera-frontend-end-2020/pull/1

Package.json was modified, updating jquery - there is a need to run "npm install" to apply those changes (afterwards jquery was updated)

Afer that:
> npm WARN bootstrap@4.0.0 requires a peer of popper.js@^1.12.9 but none was installed.

Tried:
npm install popper.js@^1.16.0 --save
(https://stackoverflow.com/questions/47039812/how-to-install-popper-js-with-bootstrap-4?rq=1)

## Bootstrap Grid System: Breakpoints

- col-sm-3 means, for sm + all sizes above sm = column with 3/12
- col-md-9, for medium (screen size ≥768px) + all screen sizes above medium = column width 9/12
> „Grid breakpoints are based on minimum width media queries, meaning they apply to that one breakpoint and all those above it (e.g., .col-sm-4 applies to small, medium, large, and extra large devices, but not the first xs breakpoint).“
https://getbootstrap.com/docs/4.0/layout/grid/

## Week1: Assignment - Hiding elements based on grid screen sizes

Hiding a div(p) only on xs (extra small) screens:

>	.d-none .d-sm-block

(d-none = hidden on all screens, d-sm-block: show this block on screen size smaller + all sizes above), See table here:
https://getbootstrap.com/docs/4.0/utilities/display/#hiding-elements

Also: Print styles
https://getbootstrap.com/docs/4.0/utilities/display/#display-in-print


## Week2

### Icon fonts:

> npm install font-awesome@4.7.0 --save
> npm install bootstrap-social@5.1.1 --save

### Forms

Grid system used in div.form-group row + label.col-md-2 + input.col-md-2 (medium screen size and above)

### Tables

dl = description list, format content inside, dt = description (list) termin (HTML5)
https://wiki.selfhtml.org/wiki/HTML/Textstrukturierung/dl
> <dl class="row">
>  <dt class="col-6">Started</dt>


### Media Object (images)
image positioned relative to content
https://getbootstrap.com/docs/4.0/layout/media-object/
- good for list of videos, articles,etc. with thumb previews

### Buttons
.btn-block for whole size of col
https://getbootstrap.com/docs/4.0/components/buttons/#sizes

## Week 3

Found out about [https://atom.io/packages/v-bootstrap4](https://atom.io/packages/v-bootstrap4) for Atom, found other nice plugins here:
[https://www.shopify.com/partners/blog/best-atom-packages](https://www.shopify.com/partners/blog/best-atom-packages)

### Modals

- Should be on top of the HTML page

### Carousel
- hiding the description / title on smaller devices is clever:

`<div class="carousel-caption d-none d-md-block">`

