## Summary of Bug Fix: Cursor Shift After First Letter

**Problem Identified:**  
The cursor was shifting to the left after entering the first letter in the text editor. This was caused by unnecessary re-renders of the `RichTextEditor` component when the parent `LogEditor` component's state changed.

**Root Cause:**

- Every keystroke updated `editorBody` state in `LogEditor`
- This state was passed as a `value` prop to `RichTextEditor`
- The component re-rendered with a new `LexicalComposer` instance on each keystroke
- Lexical's internal editor state got reset, causing cursor position loss

**Solution Implemented:**

### 1. **RichTextEditor Component** (`index.tsx`)

- Wrapped the component with `React.memo()` to prevent unnecessary re-renders
- Removed unused `isInitialMount` ref that wasn't doing anything
- Fixed indentation in the `OnChangePlugin` callback
- Ensured the component only re-initializes when absolutely necessary

### 2. **LogEditor Component** (`LogEditor.tsx`)

- Changed the `value` prop from `editorBody` (which updates on every keystroke) to `log?.body || ""`
- `log?.body` only changes when editing an existing log, not during typing
- The ref `editorBodyRef` continues to track content for form submission
- Removed the local state dependency that was causing constant re-renders

**Result:**

- The editor maintains its internal state and cursor position across keystrokes
- `memo()` prevents re-renders when parent state changes
- The Lexical editor instance remains stable while typing
- Content is still properly tracked for submission via the ref

The fix ensures the `RichTextEditor` component only re-initializes when the actual log content changes (e.g., loading a different log), not on every character typed.