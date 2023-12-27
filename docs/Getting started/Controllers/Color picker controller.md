---
sidebar_position: 6
---

# Color picker controller

In some cases, non coders or users might want to change the color of some elements on your website, eg. text color, button color, background color of your website to suit their preferences or branding. This color picker allows you to do so. It returns a string of `HEX` value to the your prop.

```jsx title="/components/blocks/HeroBlock.tsx"

type PropsT = {
  backgroundColor: string;
  textColor: string;
};

export default function HeroBlock({ backgroundColor, textColor}: PropsT) {
  return (
    <div className="text-center py-10" style={{backgroundColor: backgroundColor}}>
      <h1 className="text-4xl" style={{color: textColor}}>I'm a big hero</h1>
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
      { name: 'backgroundColor', type: 'colorPicker', label: 'Background color' },
      { name: 'textColor', type: 'colorPicker', label: 'Text color' }
    ],
    ****
  },
]
```

This should render two color pickers  in the builder controllers right side bar with the label `Background color` and `Text color`. Now you can control the color of both the background and text of the hero block.