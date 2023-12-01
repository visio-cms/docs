---
sidebar_position: 4
---

# Rich Text controller

Sometimes, you would want to display some text contents in your website with some html formatting, eg. links, bold, italic, etc. The rich text controller allows you to render such data unlike the [`textArea`](/docs/Getting%20started/Controllers/Textarea%20controller) controller which strips off this html tags.


Below shows how to implement one

```jsx title="/components/blocks/RichTextBlock.tsx"
import { RenderRichText } from 'visio-cms';

type PropsT = {
  content: string;
};

export default function RichTextBlock({ content}: PropsT) {
  return (
    <div className="text-center py-10">
       <RenderRichText htmlContent={content} />
    </div>
  );
}
```

You have to import `RenderRichText` from `visio-cms` to render the `HTML` content. This component sanitizes your html content and remove unwanted tags and malicious codes form the html. eg. scripts etc.


```jsx title="/components/blocks_registry.tsx"

import RichTextBlock from '@/components/blocks/RichTextBlock.tsx';

const registeredBlocks: Block[] = [
 *****
  {
    component: RichTextBlock
    ****
    controllers: [
      { name: 'content', type: 'richText', label: 'Content of features' }
    ],
    ****
  },
]
```


This should render a rich text editor input in the builder controllers right side bar with a label `Content of features`. Changes made to this input will automatically update the value of your `content prop`.