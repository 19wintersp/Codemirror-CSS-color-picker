# CodeMirror Color Picker

A codemirror extension that adds a color picker input next to CSS color values

![preview](https://replit.com/cdn-cgi/image/width=3840,quality=80/https://storage.googleapis.com/replit/images/1632627522442_46320608eaa3f0c58bebd5fe4a10efc2.gif)

### Usage

```ts
import { basicSetup, EditorState } from '@codemirror/basic-setup';
import { EditorView } from '@codemirror/view';
import { css } from '@codemirror/lang-css';
import { cssColorPicker } from '@replit/codemirror-css-color-picker';

new EditorView({
  parent: document.querySelector('#editor'),
  state: EditorState.create({
    doc: '.wow {\n  color: #fff;\n}',
    extensions: [
      basicSetup,
      css(),
      cssColorPicker({
        style: {
          wrapper: {
            outlineColor: 'transparent',
          },
        },
      }),
    ],
  }),
});
```

```ts
interface CSSColorPickerOptions {
  /**
   * Additional [`style-mod`](https://github.com/marijnh/style-mod#documentation)
   * style spec providing theme for the color picker.
   */
  style?: {
    /** Style spec for the color picker `<div>` container */
    wrapper?: StyleSpec;
    /** Style spec for the color picker `<input>` element */
    input?: StyleSpec;
  };
}
```

### Todos

- Investigate solutions for alpha values. `input[type="color"]` doesn't support alpha values, we could show another number input next to it for the alpha value.
