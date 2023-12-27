---
sidebar_position: 1
---

# Controllers

## Introduction

As the name goes **controllers**, these are array of elements in the builder right side bar, which are mapped to control the values of the props of your blocks. 

The number of controllers are set by you depending on the number of props you want to control or map to. A typical control is just an object which is added to the controllers  array of each block register object.

## controller object Key Meanings

```tsx
export type BlockControllers = {
  name: string;
  type: ControllerTypes;
  label: string;
  schema?: BlockControllers[];
  listDisplayedLabels?: {
    title: string;
    caption?: string;
    image?: string;
  };
};

```

- **`name`** - Reference to your prop of the block.
- **`type`** - Type of controller you want to map prop with. eg  [`image`](/docs/Getting%20started/blocks%20registry.mdx)
- **`label`** - This is the title of the controller
- **`shema`** and **`listDisplayedLabels`** are optional keys which are only needed by the [`list`](/docs/Getting%20started/blocks.md) controller type. Additionally, there might be other keys you have to add to the controller objects based on the type of controller you are using.

In our `blocks_registry` file, we added something like this
```tsx
const registeredBlocks: BlockT<CustomControllerT>[] = [
  {
    ****
    controllers: [
      { name: 'title', type: 'text', label: 'Title' },
      { name: 'subTitle', type: 'richText', label: 'Sub Title' },
      { name: 'image', type: 'image', label: 'Side Image' },
    ],
    ****
  },
]

```
