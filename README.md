# vue-top-down

[![NPM](https://nodei.co/npm/vue-top-down.png)](https://www.npmjs.com/package/vue-top-down)

`Vue` rendering is designed to be bottom-up.

There are cases where the template is not pre-defined but from a raw html, and you would like to 'mount' `Vue` components on some of the elements, with original DOM hierarchy preserved.

Check out [demo](https://moyummy.github.io/vue-top-down/example/).

## Usage

~~~javascript
import { VueTopDown, VTDConstants } from 'vue-top-down'
import OneComponent from 'path/to/one/component'
import AnotherComponent from 'path/to/another/component'

const StructComp = {
  mixins: [VueTopDown],
  components: {
    OneComponent,
    AnotherComponent
  },
  data () {
    return {
      [VTDConstants.ROOT]: '.selector.from.root.path.of.hosting.element',
      [VTDConstants.MAPPING]: {
        '.selector.for.one.component': OneComponent,
        '.selector.for.another.component': AnotherComponent
      }
    }
  }
}
~~~

~~~javascript
import { VueTopDownItem } from 'vue-top-down'

export default {
  name: 'OneComponent',
  mixins: [VueTopDownItem] // handle 'clazz' / 'outerHTML' or omit this to render independent component
}
~~~