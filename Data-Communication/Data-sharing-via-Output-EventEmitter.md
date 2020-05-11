This is another way of communicting between child and parent component. Through Ouput method you can directly emit values from child to parent 

The child component will emit the value using @Output() Directive and parent component need to receive those values.

### child component


```js 

import { Component, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'child-component',
  template: './child.component.html',
  styleUrls: ['./child.component.css']
})
export class ChildComponent {

  childCompData: string = "Hi I am from child component"

  @Output() outPutHandler = new EventEmitter<string>();

  constructor() { }

  emitDataToParent() {
    this.outPutHandler.emit(this.childCompData)
  }
}

```


Now in the parent component we need to mention output using (outPutHandler)="getData"

so in parent html we need to mention this 

#### parent.component.html

```html
<child-component (outPutHandler)="getData($event)"></child-component>
<p>
   Data from child component {{parentData}}
</p>
```


### parent.component.ts 

```js
import { Component } from "@angular/core";

@Component({
  selector: "parent-component",
  template: "./parent.component.html",
  styleUrls: ["./parent.component.css"]
})
export class ParentComponent {
  constructor() {}

  parentData: string;

  getData($event) {
    this.parentData = $event;
  }
}
```

