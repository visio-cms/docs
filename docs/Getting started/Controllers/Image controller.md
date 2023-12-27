---
sidebar_position: 7
---

# Image controller

An image controller allows you to upload images to your website, these images can also be found in your [`assets`](https://dashboard.visiocms.com/assets).
This returns on object containing some `attributes` of the image. Images are served through cloudinary and optimized. In rendering your image in your webpage, 
we recommend using the [`Image`](https://nextjs.org/docs/pages/api-reference/components/image) from `next/image` for better optimization and performance.

Uploaded images are stored and available to your project any time you need them. You can simply select them from the media explorer or modal which pops up when selecting an image.

```tsx
export type ImageT = {
  url: string | undefined;
  width: number | undefined;
  height: number | undefined;
  alt?: string;
};

```

- **`url`** - Url is the upload path of your image.
- **`width`** - Width of the image you uploaded.
- **`height`** - Height of the image you uploaded.
- **`alt`** - For SEO optimization, this can be the name or description of your image.

Let's see how we can implement an image in a block

```jsx title="/components/blocks/HeroBlock.tsx"
import { ImageT } from 'visio-cms';
import Image from 'next/image';
type PropsT = {
  avatar: ImageT;
};

export default function HeroBlock({avatar}: PropsT) {
  return (
    <div className="py-10">
        <Image 
         src={avatar?.url || ''}
         alt={avatar?.alt || ''}
         width={avatar?.width || 0}
         height={avatar?.height || 0}
        className="rounded-md m-auto"/>
    </div>
  );
}
```


```jsx title="/components/blocks_registry.tsx"

import HeroBlock from '@/components/blocks/HeroBlock';

const registeredBlocks: BlockT<CustomControllerT>[] = [
 *****
  {
    component: HeroBlock
    ****
    controllers: [
      { name: 'avatar', type: 'image', label: "CEO's Photo" }
    ],
    ****
  },
]
```

This should render an image box, where you can click to select an image from your media explorer or replace it when a new one. You can also control the width, height and alt form the image controller.