---
sidebar_position: 8
---

# Link controller
The Link Controller is a versatile control designed to facilitate the insertion of hyperlinks within your content. Content creators can leverage this controller to link elements to both internal and external pages, providing a seamless navigation experience for users.

Let's see how we can implement a in a block

```jsx title="/components/blocks/AddressBlock.tsx"
import { LinkT, RenderRichText } from 'visio-cms';

type PropsT = {
  addressLink: LinkT;
  address: string
};

export default function AddressBlock({addressLink, address}: PropsT) {
  return (
    <div className="p-10">
        <h1>Visit Us</h1>
    
        <p>Our office is located at:</p>
        
        <address>
            <RenderRichText htmlContent={address || ""} />
        </address>
        
        <p>Find us on Google Maps:</p>

        <a href={addressLink?.url} target={addressLink?.target}>View on Google Maps</a>
    </div>
  );
}
```


```jsx title="/components/blocks_registry.tsx"

import AddressBlock from '@/components/blocks/AddressBlock';

const registeredBlocks: Block[] = [
 *****
  {
    component: AddressBlock
    ****
    controllers: [
      { name: 'address', type: 'richText', label: "Company's address" },
      { name: 'addressLink', type: 'link', label: "Link to google maps address" }
    ],
    ****
  },
]
```

With this, content creators can now change their address using the rich text controller and link it to a google maps address with the link controller.

## Conclusion
The Link Controller empowers content creators to enhance their content by seamlessly integrating hyperlinks. Whether linking to internal or external pages, this tool provides a straightforward and effective means of navigation for users. Experiment with different link texts and destinations to optimize the user experience within your project.