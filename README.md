# Dynamic Cart Gift Feature for Shopify Dawn Theme

This implementation adds a dynamic gift feature to the cart page of a Shopify store using the Dawn theme. The feature allows customers to select a free gift when they meet certain criteria.

## Features

- **Cart Condition Logic**:
  - Detects if the cart contains any product from the "PremiumCollection" collection
  - OR if the cart total exceeds $100 (excluding gift products)
  - Shows the gift selection UI when either condition is met

- **Gift Product Addition**:
  - Displays a dropdown menu to select from available gift products
  - Automatically adds the selected gift to the cart at $0
  - Ensures only one gift can be added per cart

- **Gift Removal Logic**:
  - Automatically removes the gift if the cart no longer qualifies
  - Updates in real-time when cart contents change

- **Gift Access Restriction**:
  - Prevents manual addition of gift products
  - Only allows gift addition through the dynamic dropdown

- **Responsive Design**:
  - Fully responsive and matches the Dawn theme's design
  - Works on all device sizes

## Setup Instructions

### 1. Gift Product Setup

1. Create a collection named "Gifts" (URL handle must be `gifts`)
2. Add your gift products to this collection
3. Add a `gift` tag to all gift products
4. Ensure gift products are set to $0 or your desired price

### 2. Premium Collection Setup (Optional)

1. Create a collection named "PremiumCollection" (URL handle must be `premiumcollection`)
2. Add premium products to this collection

### 3. Theme Files Modified

- `snippets/main-cart-gift.liquid` - Main gift selection and display logic
- `assets/gift-feature.js` - JavaScript for gift functionality
- `layout/theme.liquid` - Added gift feature JavaScript include
- `sections/main-cart-items.liquid` - Added gift section include

### 4. Testing

1. Add products to cart to exceed $100 or add a product from the PremiumCollection
2. Verify the gift selection appears in the cart
3. Select a gift and verify it's added to the cart at $0
4. Remove items to go below $100 and verify the gift is removed
5. Test on different device sizes

## Customization

### Styling

You can customize the appearance by modifying the CSS in `snippets/main-cart-gift.liquid`. The component uses CSS variables from the Dawn theme for consistent styling.

### Gift Products

To change which products are available as gifts:
1. Add or remove products from the "Gifts" collection
2. Ensure all gift products have the `gift` tag

### Price Threshold

To change the $100 threshold:
1. Edit line 31 in `snippets/main-cart-gift.liquid`:
   ```liquid
   {%- if qualifies_by_collection or subtotal_in_dollars > 100 -%}
   ```
   Change `100` to your desired amount.

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)
- Mobile Safari (iOS 13+)
- Chrome for Android (latest)

## License

This feature is released under the MIT License. See the LICENSE file for more details.
