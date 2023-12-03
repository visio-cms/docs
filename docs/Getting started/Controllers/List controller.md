---
sidebar_position: 9
---

# List controller

## Overview

The List Controller is a versatile tool designed to empower content developers in representing a variety of list items on a web page. Whether you're creating navigation links, collections, brands, testimonials, or any other list-based content, this controller provides a flexible and easy-to-use solution.
This list controller needs additional two keys which are `schema` and `listDisplayedLabels`. **NB** A list can contain nested lists


## Properties

1. **Schema**
   - *Type:* Array of BlockControllers
   - *Description:* Defines the structure of each list item within the controller. Each item in the array represents a sub-controller, allowing for a diverse range of content types within the list.

     ```tsx
     schema: [
       { type: 'text', label: 'Title', name: 'title' },
       { type: 'text', label: 'Headline', name: 'headline' },
       { type: 'link', label: 'Link', name: 'link' },
       { type: 'image', label: 'Image', name: 'image' },
     ]
     ```

2. **List Displayed Labels**
   - *Type:* Object
   - *Description:* Specifies the labels to be displayed for each list item when rendered. This enhances the readability and clarity of the list.

     ```tsx
     listDisplayedLabels: {
       title: 'title',
       caption: 'headline',
       image: 'image',
     }
     ```

## Usage

```tsx title="/components/blocks/Collections.tsx"
import { ImageT, LinkT } from 'visio-cms';
import Image from 'next/image';

type CollectionsT = {
  title: string;
  headline: string;
  image: ImageT;
  key: string;
  link: LinkT;
};

export default function Collections({ collections, title }: { collections: CollectionsT[]; title: string }) {
  return (
    <div className="bg-gray-100">
      <div className="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <div className="mx-auto max-w-2xl py-16 sm:py-24 lg:max-w-none lg:py-32">
          <h2 className="text-2xl font-bold text-gray-900">{title}</h2>

          <div className="mt-6 space-y-12 lg:grid lg:grid-cols-3 lg:gap-x-6 lg:space-y-0">
            {collections.map((collection) => (
              <div key={collection.key} className="group relative">
                <div className="relative h-80 w-full overflow-hidden rounded-lg bg-white sm:aspect-h-1 sm:aspect-w-2 lg:aspect-h-1 lg:aspect-w-1 group-hover:opacity-75 sm:h-64">
                  <Image
                    src={collection.image?.url || ''}
                    alt={collection.image?.alt || ''}
                    fill
                    className="h-full w-full object-cover object-center"
                  />
                </div>
                <h3 className="mt-6 text-sm text-gray-500">
                  <a href={collection?.link?.url} target={collection?.link?.target}>
                    <span className="absolute inset-0" />
                    {collection.headline}
                  </a>
                </h3>
                <p className="text-base font-semibold text-gray-900">{collection.title}</p>
              </div>
            ))}
          </div>
        </div>
      </div>
    </div>
  );
}
```

```jsx title="/components/blocks_registry.tsx"

import Collections from '@/components/blocks/Collections';

const registeredBlocks: Block[] = [
 *****
  {
    component: HeroBlock
    ****,
    defaultInputs: { collections: [], title: 'Collections' },
    controllers: [
      { type: 'text', label: 'Title', name: 'title' },
      {
        name: 'collections',
        type: 'list',
        label: 'Collections',
        listDisplayedLabels: {
          title: 'title',
          caption: 'headline',
          image: 'image',
        },
        schema: [
          { type: 'text', label: 'Title', name: 'title' },
          { type: 'text', label: 'HeadLine', name: 'headline' },
          { type: 'link', label: 'Link', name: 'link' },
          { type: 'image', label: 'Image', name: 'image' },
        ],
      },
    ],
    ****
  },
]
```