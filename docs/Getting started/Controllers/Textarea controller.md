---
sidebar_position: 3
---

# Textarea controller

Unlike the text controller, which accepts a limited number of strings, the textarea accepts large chunk of strings. This can be used in your website where you want to display a sub title or a large text without html formatting. 

```jsx title="/components/blocks/TextBlock.tsx"

type PropsT = {
  content: string;
};

export default function TextareaBlock({ content}: PropsT) {
  return (
    <div className="text-center py-10">
      <p>{content}</p>
    </div>
  );
}
```


```jsx title="/components/blocks_registry.tsx"

import TextareaBlock from '@/components/blocks/TextareaBlock.tsx';

const registeredBlocks: Block[] = [
 *****
  {
    component: TextareaBlock
    ****
    controllers: [
      { name: 'content', type: 'textArea', label: 'Content of features' }
    ],
    ****
  },
]
```


This should render a textarea input in the builder controllers right side bar with a label `Content of features`. Changes made to this input will automatically update the value of your `content prop`.