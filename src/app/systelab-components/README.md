# systelab-components

systelab-components is a set of components that use wide accepted and adopted standard technologies like Angular and Bootstrap, as well as other popular libraries. Please read the ATTRIBUTION.md file for a complete list of dependencies.

Bootstrap 4 knowledge will be very useful to understand and use the library, as is based on it.
                                                    
## Using the library

In order to use the library, the first step will be to add the dependency in your package.json

```bash
npm install systelab-components --save
```

After, you must add the following styles and scripts in the angular.json file,

```javascript
"styles": [
        "../node_modules/ag-grid/dist/styles/ag-grid.css",
        "../node_modules/ag-grid/dist/styles/theme-fresh.css",
        "../node_modules/primeng/resources/themes/omega/theme.css",
        "../node_modules/primeng/resources/primeng.min.css",
        "../node_modules/systelab-components/icons/icomoon.css"
      ],
"scripts": [
        "../node_modules/jquery/dist/jquery.min.js",
        "../node_modules/popper.js/dist/umd/popper.js",
        "../node_modules/bootstrap/dist/js/bootstrap.js",
        "../node_modules/pako/dist/pako.min.js",
        "../node_modules/nanobar/nanobar.js"
      ],
```

After, you must import SystelabComponentsModule, as well as other libraries, in your Application Module:

```javascript
NgModule({
    imports: [
        BrowserModule,
        FormsModule,
        HttpClientModule,
        SystelabTranslateModule.forRoot(),
        SystelabPreferencesModule.forRoot(),
        SystelabLoginModule.forRoot(),
        SystelabComponentsModule.forRoot(),
        DndModule.forRoot(),
        AgGridModule.withComponents([
            GridContextMenuComponent,
            GridHeaderContextMenuComponent
        ]),
    ...
```

and add MessagePopupService and DialogService as providers.

```javascript
providers: [
    MessagePopupService,
    DialogService
],
```

Finally, you must import the systelab-bootstrap-settings, bootstrap and systelab-components sass files in the styles of your main component, and make them visible for all your components.

In the following example, for the component AppComponent, we have created and added the sass file app.component.scss. Also we have set the encapsulation as None.

```javascript
@Component({
    selector:      'app-root',
    templateUrl:   'app.component.html',
    styleUrls:     ['app.component.scss'],
    encapsulation: ViewEncapsulation.None
})
export class AppComponent {

    constructor(protected preferencesService: PreferencesService, protected i18nService: I18nService) {
        ...
    }
}
```

In the sass file app.component.scss, we have imported the Bootstrap and systelab-component sass styles.

```sass
@import "../systelab-components/sass/systelab-bootstrap-settings";
@import "../../../node_modules/bootstrap/scss/bootstrap";
@import "../systelab-components/sass/systelab-components";
```

Notice that the Bootstrap package is a dependency for systelab-components, and npm will download it.

### Changing the default style

To change the default Bootstrap or systelab-components settings like colors, border-radius, etc, add or change the value of the property in the scss file before importing the standard. For example:

```sass
$slab-size-percentage: 1;
$primary-color: rgb(0, 154, 181);

@import "../systelab-components/styles/sass/systelab-bootstrap-settings";
@import "../../../node_modules/bootstrap/scss/bootstrap";
@import "../systelab-components/styles/sass/systelab-components";
```

All values defined in Bootstrap [_variables.scss](https://github.com/twbs/bootstrap/blob/v4-dev/scss/_variables.scss) and systelab-components [_variables.scss](styles/sass/_variables.scss) can be overwritten here.

Anyway, think it twice before you change this settings and think in the value of having a homogeneous look and feel.

## Components

A bunch of different components and utilities are provided as part of the library. In the folder with the implementation of each component, you will find documentation about how to use it. In the showcase you will find examples. 

As this components will be placed in a container, in the following sections you will find some tips about how to do it. Please check our [application frame](applicationframe), [dialog](modal/dialog) as a base containers of the layout.

The following table summarizes all the components included in the library.

| Component | Description |
| --------- | ----------- |
| [systelab-add-remove-list](add-remove-list) | A list with elements to add and remove |
| [systelab-app-frame](applicationframe) | Application frame, using a header and a sidebar |
| [systelab-app-header](applicationframe/header) | Application header |
| [systelab-app-sidebar](applicationframe/sidebar) | Application side bar |
| [systelab-breadcrumb](breadcrumb) | Component to allows users to keep track and maintain awareness of their locations |
| [systelab-calendar-header](calendar) | Calendar header with navigation |
| [systelab-calendar-table](calendar) | Month view custom calendar |
| [systelab-colorpicker](colorpicker) | Color picker |
| [systelab-combobox](combobox) | Classes that lets you create a combo box component |
| [systelab-context-menu](contextmenu) | Context menu |
| [systelab-datepicker](datepicker) | Date picker |
| [systelab-date-time](datepicker) | Date and time picker |
| [systelab-file-selector](file-selector) | File selector |
| [systelab-grid](grid) | Classes that lets you create a grid component |
| [systelab-listbox](listbox) | Classes that lets you create a list box component |
| [systelab-loading](loading) | Widget to show that an action is being performed |
| [systelab-dialog](modal/dialog) | Classes to show a dialog |
| [systelab-message-popup](modal/message-popup) | Classes to show a popup |
| [systelab-month-selector](month-selector) | Component to show a Month Selector |
| [systelab-navbar](navbar) | Component to show a Navbar |
| [systelab-numpad](numpad) | Component to show a Numeric Keyboard dialog for an Input Text |
| [systelab-percentage-circle](percentage-circle) | Component to show a percentage indicator |
| [systelab-searcher](searcher) | Abstract classes that lets you create a Searcher component |
| [systelab-select](select) | Component to select a value form a predefined list |
| [systelab-signature-canvas](signature-canvas) | Component to show a canvas where the user can draw their signature |
| [systelab-slider](slider) | Component to select a numerical value inside a range |
| [systelab-sortable-list](sortable-list) | Abstract class that lets you create a Listbox with sortable elements |
| [systelab-spinner](spinner) | Component to select a numerical value inside a range |
| [systelab-switch](switch) | Component to select between two values |
| [systelab-tabs](tabs) | Component to show more than one panel |
| [systelab-timeline](timeline) | Component to show a vertical timeline |
| [systelab-toggle-button](toggle-button) | Component to select between two values |
| [systelab-tooltip](tooltip) | Directive to show tooltip on hover event |
| [systelab-tree](tree) | Abstract class that lets you create a Tree component |
| [systelab-twolist](twolist) | Component to select a group of elements from elements list |
| [systelab-week-selector](week-selector) | Component to show a Week Selector |
| [systelab-wizard-steps](wizard-steps) | Component to show a Wizard |



### Layout

To manage the layout, alignment, and sizing of grid columns, navigation, components, ... you can use the Bootstrap Grid or Flexbox. 

As a general tip:

- If you want to let your content control the way it is displayed, on a row by row or column by column basis, that’s flexbox.
- Or, if you want to define a grid, and either allow items to be auto-placed into the cells defined by that grid, or control their positioning using line-based positioning or grid template areas, that’s grid.

If still is not clear for you what to do, we suggest:

> Use the grid for forms or layouts where the height is defined by the components. Use flex if the height is important for you, for example when you are defining a application like layout.

For the grid, refer to https://getbootstrap.com/docs/4.0/layout/grid/.

For the Flexbox, refer to https://css-tricks.com/snippets/css/a-guide-to-flexbox/ as a general guide and check https://getbootstrap.com/docs/4.0/utilities/flex/ to better know the utility classes that Bootstrap provides.

As a super basic summary:

- Use **.d-flex** to set a flex box container. By default the container will arrange the elements in a single row. Use **flex-column** to arranges the items in a column.
- Use **justify-content-end**, **justify-content-center**, **justify-content-between**, **justify-content-around** if they are needed.
- Place your elements inside the box container and use **.slab-flex-1** in the element that you want to grow (internally applies the style flex: 1).
- Apply the same pattern to the containers that you place inside to get more complex layouts. 

In the following example, the div in the middle will grow:

```html
<div class="d-flex flex-column">
    <div class="bg-info">Info</div>
    <div class="slab-flex-1 bg-success"></div>
    <div class="bg-white">White</div>
</div>
```
Combine as needed. In this case will have elements placed in the north (info), south (white), west (warning), east (danger) and in the center (success). 

```html
<div class="d-flex flex-column">
    <div class="bg-info">Info</div>
    <div class="slab-flex-1 d-flex flex-row">
        <div class="bg-warning">Warning</div>
        <div class="slab-flex-1 bg-success">
        </div>
        <div class="bg-danger">Danger</div>
    </div>
    <div class="bg-white">White</div>
</div>
```

Use **.ml-auto** in a flex container if you want to push the item to the left. This will be helpful for example to push a button and place it to the bottom right of a dialog.

Use **.slab-overflow-container** for the element that could/should scroll. 

### Forms

Check the folder [forms](forms) to get an introduction and some examples about how to design forms forms.

### Borders

Check the Bootstrap utilities at https://getbootstrap.com/docs/4.0/utilities/borders/ to add some borders.

As a super basic summary:

Add **.border** and **.rounded**, and probably some margin classes, if you want a classical gray rounded border.
