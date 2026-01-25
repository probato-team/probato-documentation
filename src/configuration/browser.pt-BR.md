# Browser Configuration

This section describes how **browser execution is configured** in Probato.

Browser configuration controls how tests interact with the browser, including which browser is used, execution mode, and browser-specific behavior.

---

## Purpose of browser configuration

Browser configuration is responsible for:

- selecting the browser used during execution
- defining headless or headed execution
- configuring browser-specific options
- ensuring consistent behavior across environments

It does not affect test logic or scenario definition.

---

## Browser section

Browser settings are defined under the `browser` section of the configuration file.

Example:

```yaml
browser:
  name: chrome
  headless: true
  window:
    width: 1920
    height: 1080
```

---

## Available properties

### name
Defines which browser will be used.

Supported values typically include:
- `chrome`
- `firefox`

The browser must be installed on the system.

---

### headless
Controls whether the browser runs in headless mode.

- `true` — browser runs without UI
- `false` — browser UI is visible

Headless mode is recommended for CI/CD environments.

---

### window
Defines the browser window size.

Properties:
- `width`
- `height`

Setting a fixed window size ensures:
- consistent screenshots
- predictable UI behavior
- stable visual validation

---

## Browser drivers

Probato manages browser drivers automatically.

This removes the need to:
- manually install drivers
- manage driver versions
- configure driver paths

---

## Best practices

- Use headless mode for CI pipelines
- Define explicit window sizes
- Keep browser configuration consistent across environments
- Avoid browser-specific logic in test code

---

## What comes next

Continue with:

➡️ **Execution Settings** — to configure execution lifecycle and behavior
