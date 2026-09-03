# iris-ui

Three React components I keep rewriting from scratch on new projects, so I stopped rewriting
them: `Button`, `Tag`, and `Tooltip`. TypeScript, no runtime dependencies, one stylesheet you
can override with custom properties.

The point of this library is the behaviour, not the look:

- A loading button keeps `aria-busy` and stays in the tab order — it is marked with
  `aria-disabled` and swallows the click, rather than disappearing from keyboard navigation.
- `Tag`'s remove button carries a real label (`removeLabel`), not a bare `×`.
- `Tooltip` opens on hover *and* focus, closes on Escape, and wires `aria-describedby` to the
  trigger only while it is visible.
- Tone colours are a border, never the only signal.

## Install

```sh
npm install iris-ui
```

## Usage

```tsx
import { Button, Tag, Tooltip } from "iris-ui";
import "iris-ui/styles.css";

export function Toolbar() {
  return (
    <Tooltip label="Publishes to the staging environment">
      <Button variant="primary" onClick={publish}>
        Publish
      </Button>
    </Tooltip>
  );
}
```

`Button` takes `variant` (`primary | secondary | ghost`), `loading`, `disabled`, and any
native button attribute. `Tag` takes `tone`, `onRemove`, and `removeLabel`. `Tooltip` takes
`label`, `placement` (`top | bottom`), and a single focusable child.

Theme it by overriding the custom properties on any ancestor: `--iris-accent`,
`--iris-border`, `--iris-radius`, `--iris-ring`.

## Local development

```sh
npm install
npm run dev     # demo page at http://localhost:5173
npm run build   # type declarations + ESM into dist/
```

## Licence

MIT.
