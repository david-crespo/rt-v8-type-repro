# Example

To run this example:

- `npm install` or `yarn`
- `npm run start` or `yarn start`

## Cell type error

It seems this is not allowed:

```ts
const Add5Cell = ({ value }: Cell<{ Value: number }>) => value + 5;

// ...
table.createDataColumn("age", { cell: Add5Cell }),
```

```
$ npm run tsc

src/main.tsx(119,9): error TS2322: Type '({ value }: Cell<{    Value: number;}>) => number' is not assignable to type 'Renderable<Overwrite<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>, { ...; }>, { ...; }> | undefined'.
  Type '({ value }: Cell<{    Value: number;}>) => number' is not assignable to type '(props: { instance: TableInstance<Overwrite<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>, { ...; }>>; row: Row<...>; column: Column<...>; cell: Cell<...>; value: number; }) => ReactNode'.
    Types of parameters '__0' and 'props' are incompatible.
      Type '{ instance: TableInstance<Overwrite<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>, { ...; }>>; row: Row<...>; column: Column<...>; cell: Cell<...>; value: number; }' is not assignable to type 'Cell<{ Value: number; }>'.
        Type '{ instance: TableInstance<Overwrite<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>, { ...; }>>; row: Row<...>; column: Column<...>; cell: Cell<...>; value: number; }' is missing the following properties from type 'CoreCell<{ Value: number; }>': id, rowId, columnId, getCellProps, renderCell

```
