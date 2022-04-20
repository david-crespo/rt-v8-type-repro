# Example

To run this example:

- `npm install` or `yarn`
- `npm run start` or `yarn start`

## Type error

It seems this is not allowed:

```ts
export type TableProps<D> = {
  instance: TableInstance<{ Row: D }>;
};

export function Table<D>({ instance }: TableProps<D>) {
  return ( ... )
}
```

```
$ npm run tsc
> tsc
> tsc

src/main.tsx(155,14): error TS2322: Type 'TableInstance<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>' is not assignable to type 'TableInstance<{ Row: Person; }>'.
  Type 'TableInstance<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>' is not assignable to type 'TableCore<{ Row: Person; }>'.
    Types of property 'options' are incompatible.
      Type 'RequiredKeys<Options<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>, "state">' is not assignable to type 'RequiredKeys<Options<{ Row: Person; }>, "state">'.
        Type 'RequiredKeys<Options<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>, "state">' is not assignable to type 'Omit<Options<{ Row: Person; }>, "state">'.
          Types of property 'columns' are incompatible.
            Type 'ColumnDef<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>[]' is not assignable to type 'ColumnDef<{ Row: Person; }>[]'.
              Type 'ColumnDef<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>' is not assignable to type 'ColumnDef<{ Row: Person; }>'.
                Type 'ColumnDef<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>' is not assignable to type 'CoreColumnDef<{ Row: Person; }>'.
                  Types of property 'header' are incompatible.
                    Type 'Renderable<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>, { ...; }> | undefined' is not assignable to type 'Renderable<{ Row: Person; }, { instance: TableInstance<{ Row: Person; }>; header: Header<{ Row: Person; }>; column: Column<{ Row: Person; }>; }> | undefined'.
                      Type '(props: { instance: TableInstance<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>; header: Header<...>; column: Column<...>; }) => ReactNode' is not assignable to type 'Renderable<{ Row: Person; }, { instance: TableInstance<{ Row: Person; }>; header: Header<{ Row: Person; }>; column: Column<{ Row: Person; }>; }> | undefined'.
                        Type '(props: { instance: TableInstance<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>; header: Header<...>; column: Column<...>; }) => ReactNode' is not assignable to type '(props: { instance: TableInstance<{ Row: Person; }>; header: Header<{ Row: Person; }>; column: Column<{ Row: Person; }>; }) => any'.
                          Types of parameters 'props' and 'props' are incompatible.
                            Type '{ instance: TableInstance<{ Row: Person; }>; header: Header<{ Row: Person; }>; column: Column<{ Row: Person; }>; }' is not assignable to type '{ instance: TableInstance<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>; header: Header<...>; column: Column<...>; }'.
                              Types of property 'instance' are incompatible.
                                Type 'TableInstance<{ Row: Person; }>' is not assignable to type 'TableInstance<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>'.
                                  Type 'TableInstance<{ Row: Person; }>' is not assignable to type 'TableCore<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>'.
                                    Types of property 'options' are incompatible.
                                      Type 'RequiredKeys<Options<{ Row: Person; }>, "state">' is not assignable to type 'RequiredKeys<Options<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>, "state">'.
                                        Type 'RequiredKeys<Options<{ Row: Person; }>, "state">' is not assignable to type 'Omit<Options<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>, "state">'.
                                          Types of property 'columns' are incompatible.
                                            Type 'ColumnDef<{ Row: Person; }>[]' is not assignable to type 'ColumnDef<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>[]'.
                                              Type 'ColumnDef<{ Row: Person; }>' is not assignable to type 'ColumnDef<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>'.
                                                Type 'ColumnDef<{ Row: Person; }>' is not assignable to type 'CoreColumnDef<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>'.
                                                  Types of property 'header' are incompatible.
                                                    Type 'Renderable<{ Row: Person; }, { instance: TableInstance<{ Row: Person; }>; header: Header<{ Row: Person; }>; column: Column<{ Row: Person; }>; }> | undefined' is not assignable to type 'Renderable<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>, { ...; }> | undefined'.
                                                      Type '(props: { instance: TableInstance<{ Row: Person; }>; header: Header<{ Row: Person; }>; column: Column<{ Row: Person; }>; }) => any' is not assignable to type 'Renderable<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>, { ...; }> | undefined'.
                                                        Type '(props: { instance: TableInstance<{ Row: Person; }>; header: Header<{ Row: Person; }>; column: Column<{ Row: Person; }>; }) => any' is not assignable to type '(props: { instance: TableInstance<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>; header: Header<...>; column: Column<...>; }) => ReactNode'.
                                                          Types of parameters 'props' and 'props' are incompatible.
                                                            Type '{ instance: TableInstance<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>; header: Header<...>; column: Column<...>; }' is not assignable to type '{ instance: TableInstance<{ Row: Person; }>; header: Header<{ Row: Person; }>; column: Column<{ Row: Person; }>; }'.
                                                              Types of property 'header' are incompatible.
                                                                Type 'Header<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>' is not assignable to type 'Header<{ Row: Person; }>'.
                                                                  Type 'Header<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>' is not assignable to type 'CoreHeader<{ Row: Person; }>'.
                                                                    Types of property 'column' are incompatible.
                                                                      Type 'Column<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>' is not assignable to type 'Column<{ Row: Person; }>'.
                                                                        Type 'Column<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>' is not assignable to type 'CoreColumnDef<{ Row: Person; }>'.
                                                                          Types of property 'columns' are incompatible.
                                                                            Type 'ColumnDef<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>[] & Column<...>[]' is not assignable to type 'ColumnDef<{ Row: Person; }>[] | undefined'.
                                                                              Type 'ColumnDef<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>[] & Column<...>[]' is not assignable to type 'ColumnDef<{ Row: Person; }>[]'.
                                                                                The types returned by 'pop()' are incompatible between these types.
                                                                                  Type 'ColumnDef<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>> | undefined' is not assignable to type 'ColumnDef<{ Row: Person; }> | undefined'.
                                                                                    Type 'ColumnDef<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>' is not assignable to type 'ColumnDef<{ Row: Person; }> | undefined'.
                                                                                      Type 'ColumnDef<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>' is not assignable to type 'ColumnDef<{ Row: Person; }>'.
                                                                                        Type 'ColumnDef<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>' is not assignable to type 'CoreColumnDef<{ Row: Person; }>'.
                                                                                          Types of property 'header' are incompatible.
                                                                                            Type 'Renderable<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>, { ...; }> | undefined' is not assignable to type 'Renderable<{ Row: Person; }, { instance: TableInstance<{ Row: Person; }>; header: Header<{ Row: Person; }>; column: Column<{ Row: Person; }>; }> | undefined'.
                                                                                              Type '(props: { instance: TableInstance<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>; header: Header<...>; column: Column<...>; }) => ReactNode' is not assignable to type 'Renderable<{ Row: Person; }, { instance: TableInstance<{ Row: Person; }>; header: Header<{ Row: Person; }>; column: Column<{ Row: Person; }>; }> | undefined'.
                                                                                                Type '(props: { instance: TableInstance<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>; header: Header<...>; column: Column<...>; }) => ReactNode' is not assignable to type '(props: { instance: TableInstance<{ Row: Person; }>; header: Header<{ Row: Person; }>; column: Column<{ Row: Person; }>; }) => any'.
                                                                                                  Types of parameters 'props' and 'props' are incompatible.
                                                                                                    Type '{ instance: TableInstance<{ Row: Person; }>; header: Header<{ Row: Person; }>; column: Column<{ Row: Person; }>; }' is not assignable to type '{ instance: TableInstance<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>; header: Header<...>; column: Column<...>; }'.
                                                                                                      Types of property 'instance' are incompatible.
                                                                                                        Type 'TableInstance<{ Row: Person; }>' is not assignable to type 'TableInstance<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>'.
                                                                                                          Type 'TableInstance<{ Row: Person; }>' is not assignable to type 'TableCore<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>'.
                                                                                                            Types of property 'options' are incompatible.
                                                                                                              Type 'RequiredKeys<Options<{ Row: Person; }>, "state">' is not assignable to type 'RequiredKeys<Options<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>, "state">'.
                                                                                                                Type 'RequiredKeys<Options<{ Row: Person; }>, "state">' is not assignable to type 'Omit<Options<Overwrite<Overwrite<Partial<DefaultGenerics>, { Render: <TProps extends {}>(Comp: Renderable<TProps>, props: TProps) => ReactNode; }>, { ...; }>>, "state">'.
                                                                                                                  Types of property 'meta' are incompatible.
                                                                                                                    Type 'unknown' is not assignable to type 'object | undefined'.
```
