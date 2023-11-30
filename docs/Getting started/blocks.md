---
sidebar_position: 2
---

# Blocks


Consider blocks as sections that come together to form a webpage. In Visio, as a developer, your primary task is to build and export blocks, which are React components with props serving as placeholders for values controlled by the Visio sidebar controllers. These blocks can then be added by content creators and marketers to construct a webpage. With props, you have the flexibility to modify various attributes of a block. For example, you can change the styling of an element, insert and adjust an image, modify colors, adjust font size, and render lists, among other capabilities.

## Let's add a block to our website

in your `components/blocks` folder, add a new file and call it MyFirstBlock.tsx and paste the below code

```tsx title="/components/blocks/MyFirstBlock.tsx"

import Image from 'next/image';
import { ImageT, RenderRichText } from 'visio-cms';

type PropsT = {
  title: string;
  subTitle: string;
  image: ImageT;
};

export default function MyFirstBlock({ title, subTitle, image }: PropsT) {
  return (
    <div className="text-center md:flex py-10 justify-center">
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

Here, we've crafted a straightforward block with `title` and `subTitle` props. To begin utilizing this block on our website, we should register it in the `/components/blocks_registry.tsx` file. This registration process enables us to seamlessly incorporate the block into our webpages.

