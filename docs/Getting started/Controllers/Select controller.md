---
sidebar_position: 11
---

# Select controller

## Overview

Select controller offer the capability to dynamically influence the rendering of a component or apply conditional attributes based on the selected value of an option. This versatility allows you to leverage the returned value for various purposes within your application.

In the following example, we'll explore how to dynamically adjust the position of an image based on the selection of options like "left" or "right" within a select element.

## Usage

```tsx title="/components/blocks/MyFirstBlock.tsx"
import Image from 'next/image';
import { ImageT, RenderRichText } from 'visio-cms';

type PropsT = {
  title: string;
  subTitle: string;
  image: ImageT;x
  alignment: string;
};

export default function MyFirstBlock({ title, alignment, subTitle, image }: PropsT) {
  return (
    <div
      className="text-center md:flex py-10 justify-center"
      style={{ flexDirection: alignment == 'right' ? 'row-reverse' : 'row' }}
    >
      <div className="grid p-4 place-items-center mb-3 md:mb-0  md:w-1/2 flex-shrink-0">
        <div className="text-left w-full lg:p-36 ">
          <h1 className="text-4xl pb-5">{title}</h1>
          <RenderRichText htmlContent={subTitle} />
        </div>
      </div>
      <div className="w-full md:w-1/2 p-4">
        <Image
          src={image?.url || ''}
          alt={image?.alt || ''}
          width={image?.width || 0}
          height={image?.height || 0}
          className="rounded-md"
        />
      </div>
    </div>
  );
}
```

```jsx title="/components/blocks_registry.tsx"
import MyFirstBlock from '@/components/blocks/MyFirstBlock';


const registeredBlocks: BlockT<CustomControllerT>[] = [
 *****
  {
    component: MyFirstBlock,
    title: 'My First Block',
    icon: <ImageIcon />,
    defaultInputs: {
      title: 'This is my first title',
      subTitle:
        "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s",
      image: {},
      alignment: 'left',
    },
    controllers: [
      { name: 'title', type: 'text', label: 'Title' },
      { name: 'subTitle', type: 'richText', label: 'Sub Title' },
      { name: 'image', type: 'image', label: 'Side Image' },
      {
        name: 'alignment',
        type: 'select',
        label: 'Alignment',
        options: [
          {
            label: 'Left',
            value: 'left',
          },
          {
            label: 'Right',
            value: 'right',
          },
        ],
      },
    ],
    key: 'myFirstBlock',
  },
]
```

## Properties

1. **options**
   - *label:* This is the displayed text of each option 
   - *value:* This is the value each option  holds

2. **showSearch**
  This is only needed if you want to show a search input in the select.
   