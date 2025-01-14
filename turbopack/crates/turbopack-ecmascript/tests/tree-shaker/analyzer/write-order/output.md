# Items

Count: 11

## Item 1: Stmt 0, `VarDeclarator(0)`

```js
export const order = [];

```

- Declares: `order`
- Write: `order`

## Item 2: Stmt 1, `Normal`

```js
export function func() {
    order.push("d");
}

```

- Hoisted
- Declares: `func`
- Reads (eventual): `order`
- Write: `func`
- Write (eventual): `order`

## Item 3: Stmt 2, `Normal`

```js
order.push("a");

```

- Side effects
- Reads: `order`
- Write: `order`

## Item 4: Stmt 3, `VarDeclarator(0)`

```js
const x1 = externalFunction();

```

- Side effects
- Declares: `x1`
- Write: `x1`

## Item 5: Stmt 4, `VarDeclarator(0)`

```js
const x2 = externalFunction();

```

- Side effects
- Declares: `x2`
- Write: `x2`

## Item 6: Stmt 5, `VarDeclarator(0)`

```js
export const shared = {
    effect: order.push("b")
};

```

- Side effects
- Declares: `shared`
- Reads: `order`
- Write: `order`, `shared`

## Item 7: Stmt 6, `Normal`

```js
order.push("c");

```

- Side effects
- Reads: `order`
- Write: `order`

# Phase 1
```mermaid
graph TD
    Item1;
    Item2;
    Item3;
    Item4;
    Item5;
    Item6;
    Item7;
    Item8;
    Item8["ModuleEvaluation"];
    Item9;
    Item9["export order"];
    Item10;
    Item10["export func"];
    Item11;
    Item11["export shared"];
```
# Phase 2
```mermaid
graph TD
    Item1;
    Item2;
    Item3;
    Item4;
    Item5;
    Item6;
    Item7;
    Item8;
    Item8["ModuleEvaluation"];
    Item9;
    Item9["export order"];
    Item10;
    Item10["export func"];
    Item11;
    Item11["export shared"];
    Item3 --> Item1;
    Item4 --> Item3;
    Item5 --> Item4;
    Item5 --> Item3;
    Item6 --> Item3;
    Item6 --> Item1;
    Item6 --> Item5;
    Item7 --> Item6;
    Item7 --> Item1;
    Item9 --> Item7;
    Item9 --> Item1;
    Item10 --> Item2;
    Item11 --> Item6;
```
# Phase 3
```mermaid
graph TD
    Item1;
    Item2;
    Item3;
    Item4;
    Item5;
    Item6;
    Item7;
    Item8;
    Item8["ModuleEvaluation"];
    Item9;
    Item9["export order"];
    Item10;
    Item10["export func"];
    Item11;
    Item11["export shared"];
    Item3 --> Item1;
    Item4 --> Item3;
    Item5 --> Item4;
    Item5 --> Item3;
    Item6 --> Item3;
    Item6 --> Item1;
    Item6 --> Item5;
    Item7 --> Item6;
    Item7 --> Item1;
    Item9 --> Item7;
    Item9 --> Item1;
    Item10 --> Item2;
    Item11 --> Item6;
    Item2 --> Item7;
    Item2 --> Item1;
    Item2 -.-> Item9;
```
# Phase 4
```mermaid
graph TD
    Item1;
    Item2;
    Item3;
    Item4;
    Item5;
    Item6;
    Item7;
    Item8;
    Item8["ModuleEvaluation"];
    Item9;
    Item9["export order"];
    Item10;
    Item10["export func"];
    Item11;
    Item11["export shared"];
    Item3 --> Item1;
    Item4 --> Item3;
    Item5 --> Item4;
    Item5 --> Item3;
    Item6 --> Item3;
    Item6 --> Item1;
    Item6 --> Item5;
    Item7 --> Item6;
    Item7 --> Item1;
    Item9 --> Item7;
    Item9 --> Item1;
    Item10 --> Item2;
    Item11 --> Item6;
    Item2 --> Item7;
    Item2 --> Item1;
    Item2 -.-> Item9;
    Item8 --> Item7;
```
# Final
```mermaid
graph TD
    N0["Items: [ItemId(ModuleEvaluation)]"];
    N1["Items: [ItemId(Export((&quot;func&quot;, #2), &quot;func&quot;))]"];
    N2["Items: [ItemId(Export((&quot;order&quot;, #2), &quot;order&quot;))]"];
    N3["Items: [ItemId(Export((&quot;shared&quot;, #2), &quot;shared&quot;))]"];
    N4["Items: [ItemId(0, VarDeclarator(0))]"];
    N5["Items: [ItemId(1, Normal)]"];
    N6["Items: [ItemId(2, Normal), ItemId(3, VarDeclarator(0)), ItemId(4, VarDeclarator(0)), ItemId(5, VarDeclarator(0))]"];
    N7["Items: [ItemId(6, Normal)]"];
    N3 --> N6;
    N5 --> N4;
    N0 --> N7;
    N5 --> N7;
    N1 --> N5;
    N6 --> N4;
    N5 -.-> N2;
    N7 --> N6;
    N7 --> N4;
    N2 --> N7;
    N2 --> N4;
```
# Entrypoints

```
{
    ModuleEvaluation: 0,
    Export(
        "order",
    ): 2,
    Exports: 8,
    Export(
        "func",
    ): 1,
    Export(
        "shared",
    ): 3,
}
```


# Modules (dev)
## Part 0
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 7
};
"module evaluation";

```
## Part 1
```js
import { a as func } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -5
};
export { func };

```
## Part 2
```js
import { b as order } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -4
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 7
};
export { order };

```
## Part 3
```js
import { c as shared } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -6
};
export { shared };

```
## Part 4
```js
const order = [];
export { order as b } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 5
```js
import { b as order } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -4
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 7
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 2
};
function func() {
    order.push("d");
}
export { func as a } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 6
```js
import { b as order } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -4
};
order.push("a");
const x1 = externalFunction();
const x2 = externalFunction();
const shared = {
    effect: order.push("b")
};
export { x1 as d } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};
export { x2 as e } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};
export { shared as c } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 7
```js
import { b as order } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -4
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 6
};
order.push("c");

```
## Part 8
```js
export { func } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export func"
};
export { order } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export order"
};
export { shared } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export shared"
};

```
## Merged (module eval)
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 7
};
"module evaluation";

```
# Entrypoints

```
{
    ModuleEvaluation: 0,
    Export(
        "order",
    ): 2,
    Exports: 8,
    Export(
        "func",
    ): 1,
    Export(
        "shared",
    ): 3,
}
```


# Modules (prod)
## Part 0
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 7
};
"module evaluation";

```
## Part 1
```js
import { a as func } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -5
};
export { func };

```
## Part 2
```js
import { b as order } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -4
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 7
};
export { order };

```
## Part 3
```js
import { c as shared } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -6
};
export { shared };

```
## Part 4
```js
const order = [];
export { order as b } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 5
```js
import { b as order } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -4
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 7
};
function func() {
    order.push("d");
}
export { func as a } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 6
```js
import { b as order } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -4
};
order.push("a");
const x1 = externalFunction();
const x2 = externalFunction();
const shared = {
    effect: order.push("b")
};
export { x1 as d } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};
export { x2 as e } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};
export { shared as c } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 7
```js
import { b as order } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -4
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 6
};
order.push("c");

```
## Part 8
```js
export { func } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export func"
};
export { order } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export order"
};
export { shared } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export shared"
};

```
## Merged (module eval)
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 7
};
"module evaluation";

```
