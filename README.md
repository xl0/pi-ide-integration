# ide-integration

Pi package template for an IDE integration extension.

## Install

```bash
pi install npm:@xl0/ide-integration
```

Or load without installing:

```bash
pi -e npm:@xl0/ide-integration
```

## Local development

```bash
bun install
bun run check
pi -e .
```

## Structure

- `package.json` — npm and Pi package manifest
- `extensions/ide-integration/index.ts` — extension entry point
