# vue-bootalert
VueJS component for generating Bootstrap alerts

## Installation

``` bash
# install with npm
npm install vue-bootalert --save
```

``` javascript
var VueBootalert = require('vue-bootalert')
Vue.use(VueBootalert)
```
## Usage

Add as a component:

``` javascript
components: {
    VueBootalert
}
```
You can then create an alert with:

``` html
<bootalert message="Your message here"></bootalert>
```

You can configure the alert with the following parameters:

| Name  | Description |  Required | Allowed Values | Type | Default Value  |
|---|---|---|---|---|---|
| type  |  The alert style, taken from Bootstrap alert classes |  N | info, warning, success, danger  | String  |  info |
| message | The message to display in the alert | Y  | Text/HTML | String  | nil  |
| shouldDisappear  | The alert should disappear automatically after a period of time  | N | true, false  | Boolean  | true |
| displayTime  | The time in miliseconds the message should stay on screen for (if shouldDisappear is set to true)  | N |   | Integer | 5000 |
| alertDismissable  | Allow the user to close the alert by clicking on X  | N | Dismissable if present |   |  false |

## Examples

### Basic Usage

``` HTML
<bootalert type="danger" message="test message 1 (dismisable)" shouldDisappear="false" alertDismissable></bootalert>
<bootalert type="success" message="test message 2"></bootalert>
```

### Dynamically creating alerts

``` HTML
<bootalert v-for="(alert,index) in alerts" :key="index" v-bind:type="alert.type" v-bind:message="alert.message" v-bind:shouldDisappear="alert.shouldDisappear" alertDismissable></bootalert>
```

``` Javascript
export default {
    data: function() {
      return {
        alerts: []
      }
    },
    methods: {
      createErrorAlert: function(message) {
        this.alerts.push({
          type: 'danger',
          message: message,
          shouldDisappear: false
        });
      }
    }
}

// Then call createErrorAlert when you want a new message
createErrorAlert("Your message here")
```