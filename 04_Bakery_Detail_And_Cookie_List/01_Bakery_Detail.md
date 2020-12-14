Let's create a bakery detail page.

1. In your `components/` folder, create `BakeryDetai.js` and setup your component.

2. In Bakery Detail, we'll start by displaying the bakery's name and image. Create these styled components in your `styles.js` for the detail page:

   ```javascript
   export const BakeryDetailWrapper = styled.View`
     margin-top: 50;
   `;

   export const BakeryDetailImage = styled.Image`
     width: 150;
     height: 150;
   `;

   export const BakeryDetailTitle = styled.Text`
     font-weight: bold;
     font-size: 40;
   `;
   ```

3. Render them in your detail component. For now, display only the first bakery in your bakeryStore.

   ```javascript
   import React from "react";
   import bakeryStore from "../stores/bakeryStore";
   import {
     BakeryDetailTitle,
     BakeryDetailImage,
     BakeryDetailWrapper,
   } from "../styles";

   const BakeryDetail = () => {
     const bakery = bakeryStore.bakeries[0];
     return (
       <BakeryDetailWrapper>
         <BakeryDetailImage source={{ uri: bakery.image }} />
         <BakeryDetailTitle>{bakery.name}</BakeryDetailTitle>
       </BakeryDetailWrapper>
     );
   };

   export default BakeryDetail;
   ```

4. In your `App`, comment the `BakeryList` and render `BakeryDetail` instead.

5. Oh no's! It breaks! This is because the store is still requesting the bakeries from the backend, so we need to make our detail component into an observer and put an if-statement.

   ```javascript
   import { observer } from "mobx-react";

   const BakeryDetail = () => {
     const bakery = bakeryStore.bakeries[0];
     if (bakeryStore.loading) return <Spinner />;
     return (
       <BakeryDetailWrapper>
         <BakeryDetailImage source={{ uri: bakery.image }} />
         <BakeryDetailTitle>{bakery.name}</BakeryDetailTitle>
       </BakeryDetailWrapper>
     );
   };

   export default observer(BakeryDetail);
   ```