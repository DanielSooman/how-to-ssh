# how-to-ssh

To generate an SSH key for your VPS:

### Step-by-step

1. **Open Terminal** on your local machine.

2. **Generate the key pair**:

   ```bash
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```

   - `-t rsa`: key type (you can also use `ed25519`)
   - `-b 4096`: bit length (4096 is secure for RSA)
   - `-C`: comment to identify the key

3. **When prompted**:

   - File location: press **Enter** to accept default (`~/.ssh/id_rsa`) or type a path.
   - Passphrase: optional, adds security.

   
To view your **SSH public key** on the terminal:

```bash
cat ~/.ssh/id_rsa.pub
```

---

To view your **SSH private key** (not recommended unless needed):

```bash
cat ~/.ssh/id_rsa
```
⚠️ **Do not share your private key** (`id_rsa` or `id_ed25519`). Only share the `.pub` file.

Do you need to copy the public key to clipboard as well?

4. **Upload public key to VPS**:

   ```bash
   ssh-copy-id user@your-vps-ip
   ```

   Or manually:

   ```bash
   cat ~/.ssh/id_rsa.pub | ssh user@your-vps-ip "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
   ```

5. **Login using SSH key**:

   ```bash
   ssh user@your-vps-ip
   ```

---

**Note**: Make sure `sshd` on VPS allows key-based authentication.

Do you want to use `ed25519` instead of `rsa`?
