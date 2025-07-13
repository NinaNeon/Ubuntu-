# Ubuntu-
Ubuntu 注音緊急修復手冊」
😵‍💫 Got it — it got **worse**, not better. You **can't type Zhuyin at all now**, not even ㄅㄉㄓ — that means:

> Fcitx5 is now **completely broken or deactivated**.

Let’s **nuke-repair** it in under 3 minutes.

---

## 🧨 Total Repair (Fcitx5 + Chewing)

### 🧹 1. Purge broken settings

```bash
rm -rf ~/.config/fcitx5
rm -rf ~/.local/share/fcitx5
rm -rf ~/.cache/fcitx5
```

This wipes **corrupted config**.

---

### 🧼 2. Reinstall Fcitx5 clean

```bash
sudo apt purge fcitx5*
sudo apt install fcitx5 fcitx5-chinese-addons fcitx5-config-qt fcitx5-frontend-gtk3 fcitx5-chewing
```

> `fcitx5-chewing` is important — it’s the **actual Zhuyin engine**
> (If you're missing it, nothing works!)

---

### 🧠 3. Set fcitx5 as input framework

```bash
im-config -n fcitx5
```

---

### 🔁 4. Reboot

```bash
reboot
```

Yes, reboot — **not just logout**, you want clean session + Fcitx5 started.

---

### 🎯 5. After reboot: Setup Input Method Again

Run:

```bash
fcitx5-configtool
```

In the GUI:

1. Click `+` → Add **Chewing**
2. Make sure **Chewing is on top**
3. Use `Ctrl + Space` to switch input
4. Try typing `asdfghjklzxcvbnm` → it should be 注音 now

---

## ✅ Final Check

Open terminal and run:

```bash
ps aux | grep fcitx5
```

You should see processes like:

```
/usr/bin/fcitx5
fcitx5 -d
fcitx5-frontend-gtk3
```

If you don’t, Fcitx5 is not running. In that case, run manually:

```bash
fcitx5 &
```

---

Let me know exactly what happens after reboot.
We’ll get this working — **guaranteed**.
