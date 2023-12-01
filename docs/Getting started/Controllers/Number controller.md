---
sidebar_position: 5
---

# Number controller

Similar to the text controller, the number controller can be mapped to props which only accepts numbers. You can use this for soo many scenarios, eg. Display some metrics on your website, count down, even use it as a font, padding or margin size of an element in your block etc. 

```jsx title="/components/blocks/NumberBlock.tsx"

type PropsT = {
  counter: number;
};

export default function NumberBlock({ counter}: PropsT) {
  return (
    <div className="text-center py-10">
      <h1 className="text-4xl">Days left: {counter}</h1>
    </div>
  );
}
```


```jsx title="/components/blocks_registry.tsx"

import NumberBlock from '@/components/blocks/NumberBlock.tsx';

const registeredBlocks: Block[] = [
 *****
  {
    component: NumberBlock
    ****
    controllers: [
      { name: 'counter', type: 'number', label: 'Days' }
    ],
    ****
  },
]
```

This should render a number input in the builder controllers right side bar with a label `Days`. Changes made to this input will automatically update the value of your `counter prop`.