---
sidebar_position: 2
---

# Text controller

The text controller can be mapped to props which only accept strings as their value. Below is a basic usage of a text controller

```jsx title="/components/blocks/TextBlock.tsx"

type PropsT = {
  title: string;
};

export default function TextBlock({ title}: PropsT) {
  return (
    <div className="text-center py-10">
      <h1 className="text-4xl">{title}</h1>
    </div>
  );
}
```


```jsx title="/components/blocks_registry.tsx"

import TextBlock from '@/components/blocks/TextBlock';

const registeredBlocks: Block[] = [
 *****
  {
    component: TextBlock
    ****
    controllers: [
      { name: 'title', type: 'text', label: 'Title' }
    ],
    ****
  },
]
```

This should render a text input in the builder controllers right side bar with a label `Title`. Changes made to this input will automatically update the value of your `title prop`.