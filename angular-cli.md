
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




The **"Invalid Host header"** error usually happens when you're accessing your Angular app from a different hostname or IP (like in Docker, WSL2, or a dev container), and Angular's dev server (Webpack) blocks it for security reasons.

Here’s how to fix it 👇

---

## ✅ Solution: Allow All Hosts (Development Only)

Run `ng serve` with the `--disable-host-check` flag:

```bash
ng serve --disable-host-check
```

> ⚠️ This disables host checking entirely. It's fine for **local development** but **should never be used in production**.

---

## ✅ Better Solution: Use `--host` and `--public`

If you want more control (e.g., when using IPs or accessing via `localhost` in a container):

```bash
ng serve --host 0.0.0.0 --public-host localhost:4200
```

- `--host 0.0.0.0`: Binds the dev server to all interfaces.
- `--public-host`: Specifies the expected external address.

You can also use `your-ip:4200` for `--public-host`.

---

## ✅ Permanent Fix: Edit `angular.json`

If you want these settings every time you serve:

```json
"architect": {
  "serve": {
    "options": {
      "host": "0.0.0.0",
      "disableHostCheck": true
    }
  }
}
```

Add that inside your project’s `angular.json`.

---

Let me know if you're using **WSL2, Docker, or Dev Containers**, and I’ll tailor it to that setup.