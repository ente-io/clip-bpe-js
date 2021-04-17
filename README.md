# CLIP Byte Pair Encoding JavaScript Port
A JavaScript port of [OpenAI's CLIP byte-pair-encoding tokenizer](https://github.com/openai/CLIP/blob/3bee28119e6b28e75b82b811b87b56935314e6a5/clip/simple_tokenizer.py).

```js
import Tokenizer from "https://deno.land/x/clip_bpe@v0.0.2/mod.js";
let t = new Tokenizer();

t.encode("hello") // [3306]
t.encode("magnificent") // [10724]
t.encode("magnificently") // [9725, 2922]
t.decode(t.encode("HELLO")) // "hello "
t.decode(t.encode("abc123")) // "abc 1 2 3 "
st.decode(st.encode("let's see here")) // "let 's see here "
```

This encoder/decoder behaves differently to the the GPT-2/3 tokenizer (JavaScript version of that [here](https://github.com/latitudegames/GPT-3-Encoder)). For example, it doesn't preserve capital letters, as shown above.

The [Python version](https://github.com/openai/CLIP/blob/3bee28119e6b28e75b82b811b87b56935314e6a5/clip/simple_tokenizer.py) of this tokenizer uses the `ftfy` module to clean up the text before encoding it. I didn't include that module by default because the only version available in JavaScript is this one, which requires importing a full Python runtime as a WebAssembly module. If you want the `ftfy` cleaning, just clean your text with it before passing it to the `.encode()` method.

# License

To the extent that there is any original code in this repo, it is MIT Licensed, just like [openai/CLIP](https://github.com/openai/CLIP).
