[[Handlebars]]
## Basic Partials

In order to use a partial, it must be registered via `Handlebars.registerPartial`.

preparationScript[](https://handlebarsjs.com/examples/partials/basic.html)

```
Handlebars.registerPartial('myPartial', '{{prefix}}');
```

This call will register the `myPartial` partial. Partials may be precompiled and the precompiled template passed into the second parameter.

Calling the partial is done through the partial call syntax:

template[](https://handlebarsjs.com/examples/partials/basic.html)

```
{{> myPartial }}
```

Will render the partial named `myPartial`. When the partial executes, it will be run under the current execution context.

## [#](https://handlebarsjs.com/guide/partials.html#dynamic-partials)Dynamic Partials

It's possible to dynamically select the partial to be executed by using sub expression syntax.

template[](https://handlebarsjs.com/examples/partials/dynamic.html)

```
{{> (whichPartial) }}
```

Will evaluate `whichPartial` and then render the partial whose name is returned by this function.

Subexpressions do not resolve variables so `whichPartial` must be a function. If a simple variable has the partial name, it's possible to resolve it via the `lookup` helper.

template[](https://handlebarsjs.com/examples/partials/variable.html)

```
{{> (lookup . 'myVariable') }}
```

## [#](https://handlebarsjs.com/guide/partials.html#partial-contexts)Partial Contexts

It's possible to execute partials on a custom context by passing in the context to the partial call.

template[](https://handlebarsjs.com/examples/partials/other-context.html)

```
{{> myPartial myOtherContext }}
```

## [#](https://handlebarsjs.com/guide/partials.html#partial-parameters)Partial Parameters

Custom data can be passed to partials through hash parameters.

template[](https://handlebarsjs.com/examples/partials/parameters.html)

```
{{> myPartial parameter=favoriteNumber }}
```

Will set parameter to `value` when the partial runs.

This is particularly useful for exposing data from parent contexts to the partial:

template[](https://handlebarsjs.com/examples/partials/parent-context.html)

```
{{#each people}}
  {{> myPartial prefix=../prefix firstname=firstname lastname=lastname}}.
{{/each}}
```

## [#](https://handlebarsjs.com/guide/partials.html#partial-blocks)Partial Blocks

The normal behavior when attempting to render a partial that is not found is for the implementation to throw an error. If failover is desired instead, partials may be called using the block syntax.

template[](https://handlebarsjs.com/examples/partials/failover.html)

```
{{#> myPartial }}
  Failover content
{{/myPartial}}
```

Which will render `Failover content` if the `myPartial` partial is not registered.

This block syntax may also be used to pass templates to the partial, which can be executed by the specially named partial, `@partial-block`. A template of

template[](https://handlebarsjs.com/examples/partials/partial-block.html)

```
{{#> layout }}
My Content
{{/layout}}
```

with the `layout` partial containing

partial: layout[](https://handlebarsjs.com/examples/partials/partial-block.html)

```
Site Content {{> @partial-block }}
```

Would render

output[](https://handlebarsjs.com/examples/partials/partial-block.html)

```
Site Content My Content
```

When called in this manner, the block will execute under the context of the partial at the time of the call. Depthed paths and block parameters operate relative to the partial block rather than the partial template.

template[](https://handlebarsjs.com/examples/partials/partial-block-parameters.html)

```
{{#each people as |person|}}
  {{#> childEntry}}
    {{person.firstname}}
  {{/childEntry}}
{{/each}}
```

Will render `person.firstname` from this template, not the partial.

## [#](https://handlebarsjs.com/guide/partials.html#inline-partials)Inline Partials

Templates may define block scoped partials via the `inline` decorator.

template[](https://handlebarsjs.com/examples/partials/inline.html)

```
{{#*inline "myPartial"}}
  My Content
{{/inline}}
{{#each people}}
  {{> myPartial}}
{{/each}}
```

Which will render the `myPartial` partial for each child.

Each inline partial is available to the current block and all children, including execution of other partials. This allows for layout templates and similar functionality:

template[](https://handlebarsjs.com/examples/partials/inline-blocks.html)

```
{{#> layout}}
  {{#*inline "nav"}}
    My Nav
  {{/inline}}
  {{#*inline "content"}}
    My Content
  {{/inline}}
{{/layout}}
```

Where the `layout` partial may be:

partial: layout[](https://handlebarsjs.com/examples/partials/inline-blocks.html)

```
<div class="nav">
  {{> nav}}
</div>
<div class="content">
  {{> content}}
</div>
```