### Bug: Live substitute preview cannot be disabled via `inccommand=nosplit` in v0.11.3

**Description:**
In the development build `v0.11.3`, the new live, inline preview for the `:substitute` command appears to be always active. Setting the `inccommand` option to `nosplit` has no effect, making it impossible to disable the feature.

---
### Steps To Reproduce
1.  Start Neovim with a clean configuration: `nvim --clean`
2.  Enter insert mode (`i`) and type two lines of identical text:
    ```
    test
    test
    ```
3.  Return to normal mode (`<Esc>`).
4.  Explicitly set `inccommand` to disable previews: `:set inccommand=nosplit`
5.  Begin a substitute command: `:s/test/replace`
6.  Observe the buffer as you type the replacement string "replace".

---
### Expected Behavior
When typing the replacement string ("replace"), the text in the buffer should **not** change. The matches for the search pattern ("test") should remain highlighted, but no live preview of the replacement should occur, as dictated by `inccommand=nosplit`.

---
### Actual Behavior
As the replacement string is typed, the first instance of "test" in the buffer is replaced inline, character-by-character. The `inccommand=nosplit` setting is ignored. The behavior is identical to when `inccommand` is set to `split`.

---
### Neovim Version

```
NVIM v0.11.3
Build type: Release
LuaJIT 2.1.1753363358
```

### Operating System
macOS

### Additional Context
This appears to be a bug or regression related to the new inline substitution preview feature introduced in recent development builds. The feature itself works, but the mechanism to control or disable it seems to be broken or not fully implemented.


There is also a video `recording.mov` in the doc root with this file.
