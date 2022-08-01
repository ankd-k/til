# infer

## infer is 何

inference「推論」。  
Conditional Types の条件式の中で型を推論する時に使う。

例：配列から配列の中身を型として定義できる。

```typescript
export const QUERY_KEYS = ["users", "post", "comments"] as const;
// typeof QUERY_KEYS = readonly ["users", "post", "comments"];
export type Unpacked<T> = T extends { [K in keyof T]: infer U } ? U : never;
export type QueryKeysTypes = Unpacked<typeof QUERY_KEYS>;
// type QueryKeysTypes = "users" | "post" | "comments";
```

## ref

- [Type inference in conditional types - TypeScript](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-2-8.html#type-inference-in-conditional-types)
- [【TypeScript】 infer に詳しくなろう - Qiita](https://qiita.com/ehika/items/8f41d4a3c8f9df4af9c3)
- [TypeScript の infer を今度こそちゃんと理解する - Zenn](https://zenn.dev/brachio_takumi/articles/464106a6a80eca8ab919)
