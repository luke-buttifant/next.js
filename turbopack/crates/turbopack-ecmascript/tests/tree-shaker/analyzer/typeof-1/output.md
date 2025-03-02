# Items

Count: 9

## Item 1: Stmt 0, `ImportOfModule`

```js
import { NextResponse } from 'next/server';

```

- Hoisted
- Side effects

## Item 2: Stmt 0, `ImportBinding(0)`

```js
import { NextResponse } from 'next/server';

```

- Hoisted
- Declares: `NextResponse`

## Item 3: Stmt 1, `ImportOfModule`

```js
import { ClientComponent } from '../../ClientComponent';

```

- Hoisted
- Side effects

## Item 4: Stmt 1, `ImportBinding(0)`

```js
import { ClientComponent } from '../../ClientComponent';

```

- Hoisted
- Declares: `ClientComponent`

## Item 5: Stmt 2, `ImportOfModule`

```js
import { MyModuleClientComponent } from 'my-module/MyModuleClientComponent';

```

- Hoisted
- Side effects

## Item 6: Stmt 2, `ImportBinding(0)`

```js
import { MyModuleClientComponent } from 'my-module/MyModuleClientComponent';

```

- Hoisted
- Declares: `MyModuleClientComponent`

## Item 7: Stmt 3, `Normal`

```js
export function GET() {
    return NextResponse.json({
        clientComponent: typeof ClientComponent,
        myModuleClientComponent: typeof MyModuleClientComponent
    });
}

```

- Hoisted
- Declares: `GET`
- Reads (eventual): `NextResponse`, `ClientComponent`, `MyModuleClientComponent`
- Write: `GET`
- Write (eventual): `NextResponse`

# Phase 1
```mermaid
graph TD
    Item1;
    Item4;
    Item2;
    Item5;
    Item3;
    Item6;
    Item7;
    Item8;
    Item8["ModuleEvaluation"];
    Item9;
    Item9["export GET"];
    Item2 --> Item1;
    Item3 --> Item2;
```
# Phase 2
```mermaid
graph TD
    Item1;
    Item4;
    Item2;
    Item5;
    Item3;
    Item6;
    Item7;
    Item8;
    Item8["ModuleEvaluation"];
    Item9;
    Item9["export GET"];
    Item2 --> Item1;
    Item3 --> Item2;
    Item9 --> Item7;
```
# Phase 3
```mermaid
graph TD
    Item1;
    Item4;
    Item2;
    Item5;
    Item3;
    Item6;
    Item7;
    Item8;
    Item8["ModuleEvaluation"];
    Item9;
    Item9["export GET"];
    Item2 --> Item1;
    Item3 --> Item2;
    Item9 --> Item7;
    Item7 --> Item4;
    Item7 --> Item5;
    Item7 --> Item6;
```
# Phase 4
```mermaid
graph TD
    Item1;
    Item4;
    Item2;
    Item5;
    Item3;
    Item6;
    Item7;
    Item8;
    Item8["ModuleEvaluation"];
    Item9;
    Item9["export GET"];
    Item2 --> Item1;
    Item3 --> Item2;
    Item9 --> Item7;
    Item7 --> Item4;
    Item7 --> Item5;
    Item7 --> Item6;
    Item8 --> Item3;
```
# Final
```mermaid
graph TD
    N0["Items: [ItemId(ModuleEvaluation)]"];
    N1["Items: [ItemId(Export((&quot;GET&quot;, #2), &quot;GET&quot;))]"];
    N2["Items: [ItemId(0, ImportOfModule)]"];
    N3["Items: [ItemId(0, ImportBinding(0))]"];
    N4["Items: [ItemId(1, ImportOfModule)]"];
    N5["Items: [ItemId(1, ImportBinding(0))]"];
    N6["Items: [ItemId(2, ImportOfModule)]"];
    N7["Items: [ItemId(2, ImportBinding(0))]"];
    N8["Items: [ItemId(3, Normal)]"];
    N4 --> N2;
    N6 --> N4;
    N1 --> N8;
    N8 --> N3;
    N8 --> N5;
    N8 --> N7;
    N0 --> N6;
    N3 --> N2;
    N5 --> N4;
    N7 --> N6;
```
# Entrypoints

```
{
    ModuleEvaluation: 0,
    Exports: 9,
    Export(
        "GET",
    ): 1,
}
```


# Modules (dev)
## Part 0
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 6
};
"module evaluation";

```
## Part 1
```js
import { a as GET } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -8
};
export { GET };

```
## Part 2
```js
import 'next/server';

```
## Part 3
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 2
};
import { NextResponse } from 'next/server';
export { NextResponse as b } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 4
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 2
};
import '../../ClientComponent';

```
## Part 5
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 4
};
import { ClientComponent } from '../../ClientComponent';
export { ClientComponent as c } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 6
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 4
};
import 'my-module/MyModuleClientComponent';

```
## Part 7
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 6
};
import { MyModuleClientComponent } from 'my-module/MyModuleClientComponent';
export { MyModuleClientComponent as d } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 8
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 6
};
import { MyModuleClientComponent } from 'my-module/MyModuleClientComponent';
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 2
};
import { NextResponse } from 'next/server';
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 4
};
import { ClientComponent } from '../../ClientComponent';
function GET() {
    return NextResponse.json({
        clientComponent: typeof ClientComponent,
        myModuleClientComponent: typeof MyModuleClientComponent
    });
}
export { GET as a } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 9
```js
export { GET } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export GET"
};

```
## Merged (module eval)
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 6
};
"module evaluation";

```
# Entrypoints

```
{
    ModuleEvaluation: 0,
    Exports: 9,
    Export(
        "GET",
    ): 1,
}
```


# Modules (prod)
## Part 0
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 6
};
"module evaluation";

```
## Part 1
```js
import { a as GET } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: -8
};
export { GET };

```
## Part 2
```js
import 'next/server';

```
## Part 3
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 2
};
import { NextResponse } from 'next/server';
export { NextResponse as b } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 4
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 2
};
import '../../ClientComponent';

```
## Part 5
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 4
};
import { ClientComponent } from '../../ClientComponent';
export { ClientComponent as c } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 6
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 4
};
import 'my-module/MyModuleClientComponent';

```
## Part 7
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 6
};
import { MyModuleClientComponent } from 'my-module/MyModuleClientComponent';
export { MyModuleClientComponent as d } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 8
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 6
};
import { MyModuleClientComponent } from 'my-module/MyModuleClientComponent';
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 2
};
import { NextResponse } from 'next/server';
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 4
};
import { ClientComponent } from '../../ClientComponent';
function GET() {
    return NextResponse.json({
        clientComponent: typeof ClientComponent,
        myModuleClientComponent: typeof MyModuleClientComponent
    });
}
export { GET as a } from "__TURBOPACK_VAR__" assert {
    __turbopack_var__: true
};

```
## Part 9
```js
export { GET } from "__TURBOPACK_PART__" assert {
    __turbopack_part__: "export GET"
};

```
## Merged (module eval)
```js
import "__TURBOPACK_PART__" assert {
    __turbopack_part__: 6
};
"module evaluation";

```
