# \<blockcerts-universal-verifier\>

A standalone universal viewer &amp; verifier for blockcerts credentials

# Production
The component is developed with Polymer 3.
To use the component in your project, install it via:

- TBD

Then just add it into your project with:

```html
  <blockcerts-universal-verifier></blockcerts-universal-verifier>
```

Have a look at the [Demo Pages](/demo) to see examples of the usage

## API Usage

### Default behavior
By the default, the component will:
- Display a Blockcerts record in `card` mode (concise information)
- Will allow verification of a Blockcerts Record
- Enables auto-verification (verification as the record is loaded)

### API
The component will understand the following options:

- `allow-download`: (Boolean. default: `false`). Enables the download of the record. At this moment only records provided by Learning Machine are downloadable. 
   
   Example:
   
   ```html
   <blockcerts-universal-verifier allow-download></blockcerts-universal-verifier>
   ```
- `allow-social-share`: (Boolean. default: `false`). Allows sharing the record on the social networks (LinkedIn, Facebook and Twitter). 
   
   Example:
   
   ```html
   <blockcerts-universal-verifier allow-social-share></blockcerts-universal-verifier>
   ```
- `disable-auto-verify`: (Boolean. default: `false`). Disables starting automatically the verification sequence as the record is loaded. 
   
   Example:
   
   ```html
   <blockcerts-universal-verifier disable-auto-verify></blockcerts-universal-verifier>
   ```
- `disable-verify`: (Boolean. default: `false`). Disables verification of the record altogether. 
  
  Example:
  
  ```html
  <blockcerts-universal-verifier disable-auto-verify></blockcerts-universal-verifier>
  ```
- `display-mode`: (String, oneOf('card', 'full'). default: `card`). Changes the display of a record. `card` will be a concise summary of the record with a link to the full record, while `full` will show the actual record as designed by the emitter.  
  
  Example:
  
  ```html
  <blockcerts-universal-verifier display-mode="full"></blockcerts-universal-verifier>
  ```
- `show-metadata`: (Boolean. default: `false`). Enables showing the metadata of a record.  
  
  Example:
  
  ```html
  <blockcerts-universal-verifier show-metadata></blockcerts-universal-verifier>
  ```
- `src`: (String. default: `''`). Allows loading an initial record with no further actions required. `src` can be either an absolute URL, or a relative path.  
  
  Example:
  
  ```html
  <blockcerts-universal-verifier src='../fixtures/valid-certificate-example.json'></blockcerts-universal-verifier>
  ```
  
## Event Tracking API
The component will emit events on different moment of the certificate life cycle.
To subscribe and track these events you should add on your consumer page event listeners on the `window` object.

See the [event demo page](https://github.com/learningmachine/blockcerts-universal-verifier/blob/master/demo/on-load-event.html) for a working example.

The information is communicated via the `detail` key of the event.

Supported Events:
- `certificate-load`
   
   Triggered when a certificate has been loaded into the component.
   Returns the `uid` of the certificate as a string.
   

# Development
## Viewing Your Element

```
npm run start
```

Will make the demo page available on http://localhost:8081/demo/. 

## Running Tests

### Application Tests

```
npm run test:application
```

NOTE: application must be started to run the tests, or at the very least the mock-server via the `npm run start:mock-server` (automatically included in the `npm run start` command).

**watch mode**

```
npm run test:application:watch
```

### Component Tests
```
npm run test:components
```

**"watch" mode**
```
npm run test:components:persist
```
Will allow refreshing the test page: http://localhost:8000/components/blockcerts-universal-verifier/generated-index.html?cli_browser_id=0

## Dealing with CSS
The `npm run start` command will also start a SASS compiler watcher, which means that any stylesheet within the `components` folder will be transpiled to a polymer component that can be reused within another component. ie:

```javascript
import CSS from './_components.button-css';
[...]
_render () {
    return html`${CSS}[...]`
}
```

### Using shared styles
To reduce the amount of code duplication, and following the ITCSS philosophy, you may need to import some of the shared-styles in your component.
To do so, in your component's SASS file, add the following instruction:

```javascript
/* in _components.my-component.sass */

@import '../../../shared-styles/objects.text';

[...component styles]

@import '../../../shared-styles/utils.a11y';
```

Please note that the SASS watcher does not observe changes in the shared styles folder, and will not automatically recompile any consumer stylesheet. You will have to recompile them yourselves (TODO: improve DevX here).

## More info
Please have a look through the [ADR](/docs/ADR) documentation to get more context around the architecture and the ways of developing a component.
