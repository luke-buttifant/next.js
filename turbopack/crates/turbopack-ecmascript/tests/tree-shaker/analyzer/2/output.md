# Items

Count: 19

## Item 1: Stmt 0, `Normal`

```js
export function external1() {
    return internal() + foobar;
}

```

- Hoisted
- Declares: `external1`
- Reads (eventual): `internal`, `foobar`
- Write: `external1`

## Item 2: Stmt 1, `ImportOfModule`

```js
import { upper } from "module";

```

- Hoisted
- Side effects

## Item 3: Stmt 1, `ImportBinding(0)`

```js
import { upper } from "module";

```

- Hoisted
- Declares: `upper`

## Item 4: Stmt 2, `VarDeclarator(0)`

```js
export let foobar = "foo";

```

- Declares: `foobar`
- Write: `foobar`

## Item 5: Stmt 3, `VarDeclarator(0)`

```js
export const foo = foobar;

```

- Declares: `foo`
- Reads: `foobar`
- Write: `foo`

## Item 6: Stmt 4, `VarDeclarator(0)`

```js
const bar = "bar";

```

- Declares: `bar`
- Write: `bar`

## Item 7: Stmt 5, `Normal`

```js
foobar += bar;

```

- Reads: `bar`, `foobar`
- Write: `foobar`

## Item 8: Stmt 6, `VarDeclarator(0)`

```js
let foobarCopy = foobar;

```

- Declares: `foobarCopy`
- Reads: `foobar`
- Write: `foobarCopy`

## Item 9: Stmt 7, `Normal`

```js
foobar += "foo";

```

- Reads: `foobar`
- Write: `foobar`

## Item 10: Stmt 8, `Normal`

```js
console.log(foobarCopy);

```

- Side effects
- Reads: `foobarCopy`

## Item 11: Stmt 9, `Normal`

```js
foobarCopy += "Unused";

```

- Reads: `foobarCopy`
- Write: `foobarCopy`

## Item 12: Stmt 10, `Normal`

```js
function internal() {
    return upper(foobar);
}

```

- Hoisted
- Declares: `internal`
- Reads (eventual): `upper`, `foobar`
- Write: `internal`

## Item 13: Stmt 11, `Normal`

```js
export function external2() {
    foobar += ".";
}

```

- Hoisted
- Declares: `external2`
- Write: `external2`
- Write (eventual): `foobar`

## Item 14: Stmt 12, `ImportOfModule`

```js
import "other";

```

- Hoisted
- Side effects

# Phase 1
```mermaid
graph TD
    Item3;
    Item1;
    Item4;
    Item5;
    Item6;
    Item7;
    Item8;
    Item9;
    Item10;
    Item11;
    Item12;
    Item13;
    Item14;
    Item2;
    Item15;
    Item15["ModuleEvaluation"];
    Item16;
    Item16["export external1"];
    Item17;
    Item17["export foobar"];
    Item18;
    Item18["export foo"];
    Item19;
    Item19["export external2"];
    Item2 --> Item1;
```
# Phase 2
```mermaid
graph TD
    Item3;
    Item1;
    Item4;
    Item5;
    Item6;
    Item7;
    Item8;
    Item9;
    Item10;
    Item11;
    Item12;
    Item13;
    Item14;
    Item2;
    Item15;
    Item15["ModuleEvaluation"];
    Item16;
    Item16["export external1"];
    Item17;
    Item17["export foobar"];
    Item18;
    Item18["export foo"];
    Item19;
    Item19["export external2"];
    Item2 --> Item1;
    Item6 --> Item5;
    Item8 --> Item7;
    Item8 --> Item5;
    Item8 -.-> Item6;
    Item9 --> Item8;
    Item9 --> Item5;
    Item10 --> Item8;
    Item10 --> Item5;
    Item10 -.-> Item9;
    Item11 --> Item9;
    Item11 --> Item2;
    Item11 -.-> Item13;
    Item11 --> Item10;
    Item11 -.-> Item4;
    Item12 --> Item9;
    Item12 -.-> Item11;
    Item16 --> Item3;
    Item17 --> Item10;
    Item17 --> Item5;
    Item18 --> Item6;
    Item19 --> Item14;
```
# Phase 3
```mermaid
graph TD
    Item3;
    Item1;
    Item4;
    Item5;
    Item6;
    Item7;
    Item8;
    Item9;
    Item10;
    Item11;
    Item12;
    Item13;
    Item14;
    Item2;
    Item15;
    Item15["ModuleEvaluation"];
    Item16;
    Item16["export external1"];
    Item17;
    Item17["export foobar"];
    Item18;
    Item18["export foo"];
    Item19;
    Item19["export external2"];
    Item2 --> Item1;
    Item6 --> Item5;
    Item8 --> Item7;
    Item8 --> Item5;
    Item8 -.-> Item6;
    Item9 --> Item8;
    Item9 --> Item5;
    Item10 --> Item8;
    Item10 --> Item5;
    Item10 -.-> Item9;
    Item11 --> Item9;
    Item11 --> Item2;
    Item11 -.-> Item13;
    Item11 --> Item10;
    Item11 -.-> Item4;
    Item12 --> Item9;
    Item12 -.-> Item11;
    Item16 --> Item3;
    Item17 --> Item10;
    Item17 --> Item5;
    Item18 --> Item6;
    Item19 --> Item14;
    Item3 --> Item13;
    Item3 --> Item10;
    Item3 --> Item5;
    Item13 --> Item4;
    Item13 --> Item10;
    Item13 --> Item5;
    Item14 -.-> Item17;
    Item14 --> Item5;
```
# Phase 4
```mermaid
graph TD
    Item3;
    Item1;
    Item4;
    Item5;
    Item6;
    Item7;
    Item8;
    Item9;
    Item10;
    Item11;
    Item12;
    Item13;
    Item14;
    Item2;
    Item15;
    Item15["ModuleEvaluation"];
    Item16;
    Item16["export external1"];
    Item17;
    Item17["export foobar"];
    Item18;
    Item18["export foo"];
    Item19;
    Item19["export external2"];
    Item2 --> Item1;
    Item6 --> Item5;
    Item8 --> Item7;
    Item8 --> Item5;
    Item8 -.-> Item6;
    Item9 --> Item8;
    Item9 --> Item5;
    Item10 --> Item8;
    Item10 --> Item5;
    Item10 -.-> Item9;
    Item11 --> Item9;
    Item11 --> Item2;
    Item11 -.-> Item13;
    Item11 --> Item10;
    Item11 -.-> Item4;
    Item12 --> Item9;
    Item12 -.-> Item11;
    Item16 --> Item3;
    Item17 --> Item10;
    Item17 --> Item5;
    Item18 --> Item6;
    Item19 --> Item14;
    Item3 --> Item13;
    Item3 --> Item10;
    Item3 --> Item5;
    Item13 --> Item4;
    Item13 --> Item10;
    Item13 --> Item5;
    Item14 -.-> Item17;
    Item14 --> Item5;
    Item15 --> Item11;
```
# Final
```mermaid
graph TD
    N0["Items: [ItemId(ModuleEvaluation)]"];
    N1["Items: [ItemId(Export((&quot;external1&quot;, #2), &quot;external1&quot;)), ItemId(0, Normal)]"];
    N2["Items: [ItemId(Export((&quot;external2&quot;, #2), &quot;external2&quot;)), ItemId(Export((&quot;foobar&quot;, #2), &quot;foobar&quot;)), ItemId(11, Normal)]"];
    N3["Items: [ItemId(Export((&quot;foo&quot;, #2), &quot;foo&quot;))]"];
    N4["Items: [ItemId(1, ImportOfModule)]"];
    N5["Items: [ItemId(1, ImportBinding(0))]"];
    N6["Items: [ItemId(2, VarDeclarator(0))]"];
    N7["Items: [ItemId(3, VarDeclarator(0))]"];
    N8["Items: [ItemId(4, VarDeclarator(0)), ItemId(5, Normal)]"];
    N9["Items: [ItemId(6, VarDeclarator(0))]"];
    N10["Items: [ItemId(7, Normal)]"];
    N11["Items: [ItemId(8, Normal), ItemId(12, ImportOfModule)]"];
    N12["Items: [ItemId(9, Normal)]"];
    N13["Items: [ItemId(10, Normal)]"];
    N11 --> N4;
    N7 --> N6;
    N13 --> N5;
    N8 --> N6;
    N8 -.-> N7;
    N9 --> N8;
    N9 --> N6;
    N10 --> N8;
    N10 --> N6;
    N10 -.-> N9;
    N11 --> N9;
    N1 --> N13;
    N11 -.-> N13;
    N11 --> N10;
    N11 -.-> N5;
    N12 --> N9;
    N12 -.-> N11;
    N2 --> N6;
    N13 --> N6;
    N0 --> N11;
    N3 --> N7;
    N5 --> N4;
    N13 --> N10;
    N1 --> N6;
    N1 --> N10;
```
# Entrypoints

```
{
    ModuleEvaluation: 0,
    Export(
        "external1",
    ): 1,
    Exports: 14,
    Export(
        "foo",
    ): 3,
    Export(
        "foobar",
    ): 2,
    Export(
        "external2",
    ): 2,
}
```


# Modules (dev)
## Part 0
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 11
};
"module evaluation";

```
## Part 1
```js
import { a as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -6
};
import { b as internal } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -13
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 10
};
export { external1 };
function external1() {
    return internal() + foobar;
}
export { external1 as c } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 2
```js
import { a as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -6
};
export { external2 };
export { foobar };
function external2() {
    foobar += ".";
}
export { external2 as d } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 3
```js
import { e as foo } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -7
};
export { foo };

```
## Part 4
```js
import "module";

```
## Part 5
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 4
};
import { upper } from "module";
export { upper as f } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 6
```js
let foobar = "foo";
export { foobar as a } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 7
```js
import { a as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -6
};
const foo = foobar;
export { foo as e } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 8
```js
import { a as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -6
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 7
};
const bar = "bar";
foobar += bar;
export { bar as g } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 9
```js
import { a as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -6
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 8
};
let foobarCopy = foobar;
export { foobarCopy as h } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 10
```js
import { a as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -6
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 8
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 9
};
foobar += "foo";

```
## Part 11
```js
import { h as foobarCopy } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -9
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 4
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 13
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 10
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 5
};
console.log(foobarCopy);
import "other";

```
## Part 12
```js
import { h as foobarCopy } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -9
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 11
};
foobarCopy += "Unused";

```
## Part 13
```js
import { a as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -6
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 4
};
import { upper } from "module";
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 10
};
function internal() {
    return upper(foobar);
}
export { internal as b } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 14
```js
export { external1 } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export external1"
};
export { external2 } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export external2"
};
export { foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export foobar"
};
export { foo } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export foo"
};

```
## Merged (module eval)
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 11
};
"module evaluation";

```
# Entrypoints

```
{
    ModuleEvaluation: 0,
    Export(
        "external1",
    ): 1,
    Exports: 12,
    Export(
        "foo",
    ): 3,
    Export(
        "foobar",
    ): 4,
    Export(
        "external2",
    ): 2,
}
```


# Modules (prod)
## Part 0
```js
import { a as foobarCopy } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -9
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 10
};
"module evaluation";
console.log(foobarCopy);
import "other";

```
## Part 1
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 5
};
import { upper } from "module";
import { b as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -7
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 10
};
export { external1 };
function external1() {
    return internal() + foobar;
}
function internal() {
    return upper(foobar);
}
export { external1 as c } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};
export { internal as d } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 2
```js
import { b as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -7
};
export { external2 };
function external2() {
    foobar += ".";
}
export { external2 as e } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 3
```js
import { b as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -7
};
export { foo };
const foo = foobar;
export { foo as f } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 4
```js
import { b as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -7
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 10
};
export { foobar };

```
## Part 5
```js
import "module";

```
## Part 6
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 5
};
import { upper } from "module";
export { upper as g } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 7
```js
let foobar = "foo";
export { foobar as b } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 8
```js
import { b as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -7
};
const bar = "bar";
foobar += bar;
export { bar as h } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 9
```js
import { b as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -7
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 8
};
let foobarCopy = foobar;
export { foobarCopy as a } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 10
```js
import { b as foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -7
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 8
};
foobar += "foo";

```
## Part 11
```js
import { a as foobarCopy } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -9
};
foobarCopy += "Unused";

```
## Part 12
```js
export { external1 } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export external1"
};
export { external2 } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export external2"
};
export { foo } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export foo"
};
export { foobar } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export foobar"
};

```
## Merged (module eval)
```js
import { a as foobarCopy } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -9
};
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 10
};
import "other";
"module evaluation";
console.log(foobarCopy);

```
