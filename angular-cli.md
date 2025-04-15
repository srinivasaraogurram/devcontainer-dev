
To **install Angular CLI on Ubuntu** and ensure it's available in your `PATH` (so you can run `ng` from anywhere), follow these steps:

---

### ✅ 1. **Install Angular CLI Globally**
First, install it with `npm`:

```bash
npm install -g @angular/cli
```

This installs `ng` globally, typically into a directory like:

```
/usr/local/bin/ng
```

---

### ✅ 2. **Ensure Global npm Bin Directory is in PATH**
If `ng` is not found after installation, check where it was installed:

```bash
npm bin -g
```

You'll get something like:

```
/home/youruser/.npm-global/bin
```

If that’s the case, add it to your `PATH`.

---

### ✅ 3. **Add npm Global Bin to PATH**

Add this line to your shell config file (`.bashrc`, `.zshrc`, or `.profile`):

```bash
export PATH="$PATH:$(npm bin -g)"
```

Then, apply the change:

```bash
source ~/.bashrc  # or source ~/.zshrc
```

---

### ✅ 4. **Verify It Works**

Check that `ng` is accessible:

```bash
ng version
```

You should see Angular CLI details.

---

Let me know if you’re using `nvm`, a specific Node version manager, or want this for all users (system-wide), and I can tailor the steps further.