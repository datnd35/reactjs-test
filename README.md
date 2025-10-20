### project structure

```
interview-test/
├─ package.json
├─ tsconfig.json
├─ yarn.lock / package-lock.json
├─ README.md
└─ src/
   ├─ index.tsx                # Entry chính (React 18 root)
   ├─ index.css
   ├─ reportWebVitals.js       # (tuỳ chọn) đo hiệu năng
   ├─ App.tsx                  # App root -> render AppShell
   ├─ App.css
   ├─ logo.svg

   ├─ app/
   │  ├─ AppShell.tsx          # Khung ứng dụng: Header + main + footer, wrap StoreProvider
   │  ├─ Header/
   │  │  ├─ CartIconBadge.tsx  # (nếu có) Hiển thị số lượng giỏ
   │  │  └─ ThemeSwitch.tsx    # (nếu có) Chuyển theme
   │  ├─ Main/
   │  │  ├─ CartDrawer.tsx     # (nếu có) Ngăn kéo giỏ hàng
   │  │  └─ InventoryPage/
   │  │     ├─ InventoryList/InventoryItemCard/
   │  │     │  ├─ AddToCartButton.tsx
   │  │     │  └─ StockBadge.tsx
   │  │     └─ (các component phụ khác nếu có)
   │  └─ routes/
   │     └─ InventoryPage.tsx  # Trang liệt kê sản phẩm (gọi AddToCartButton, StockBadge)

   └─ store/
      ├─ context.tsx           # StoreProvider, useStore(), useCartSummary()
      ├─ reducer.ts            # Xử lý Action: ADD_ITEM, UPDATE_QTY, REMOVE_ITEM, TOGGLE_CART, HYDRATE_INVENTORY
      ├─ selectors.ts          # selectCartSubtotal, selectCartCount, selectInventoryAvailable, ...
      ├─ types.ts              # Kiểu State, Action, InventoryItem, CartItem
      ├─ validators.ts         # (nếu có) validate dữ liệu/inputs
      ├─ cart.slice.ts         # (tuỳ chọn) slice tách nhỏ logic cart
      └─ inventory.slice.ts    # (tuỳ chọn) slice tách nhỏ logic inventory
```

### Gợi ý tổ chức & quy ước
* **app/**: UI/view + layout.
* **store/**: state global (Context + Reducer + selectors).
* **routes/**: mỗi trang một file/thư mục.
* **components dùng lại** (nếu nhiều): có thể tạo `src/components/` dùng chung thay vì lồng sâu trong `app/Main/...`.

