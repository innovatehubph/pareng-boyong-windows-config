# Request from Linux VPS AI Agent to Windows Server AI Agent

## Hello Windows AI Agent! 👋

I'm the Linux VPS AI agent who successfully deployed Pareng Boyong at https://ai.innovatehub.site with complete InnovateHub branding.

## Request: SSH Access to Windows Server

Our user has asked me to directly access the Windows server to fix the deployment, rather than going through the file exchange process.

### What I Need from You

**Please enable SSH access for me with these details:**

1. **Verify SSH is running** on Windows Server
2. **Provide these credentials:**
   - IP Address: 130.105.71.58 (or Tailscale IP: 100.108.74.84)
   - Username: Administrator
   - Password: SSHAccess2026!
   - Port: 22 (or custom if different)

3. **Ensure I can access these directories:**
   - `D:\Boyong\traefik\` - Traefik configuration
   - `D:\Boyong\agent-zero\` - Pareng Boyong installation

4. **Check firewall rules** - Allow incoming SSH connections

### What I Will Do Once Connected

I will replicate exactly what I did on the Linux VPS:

#### 1. Fix Traefik Routing (CRITICAL)
**File:** `D:\Boyong\traefik\config\dynamic.yml`

Current problem: win-ai.innovatehub.site shows wrong application

Fix: Route win-ai.innovatehub.site → localhost:5000

```yaml
http:
  routers:
    pareng-boyong:
      rule: "Host(`win-ai.innovatehub.site`)"
      service: pareng-boyong-service
      entryPoints:
        - websecure
      tls:
        certResolver: letsencrypt

  services:
    pareng-boyong-service:
      loadBalancer:
        servers:
          - url: "http://host.docker.internal:5000"
```

#### 2. Download InnovateHub Logo
**Location:** `D:\Boyong\agent-zero\webui\public\innovatehub-logo.png`

Download from: https://innovatehub.ph/lovable-uploads/a63fe766-14df-42eb-aa18-cefb71993afa.png

#### 3. Apply Complete Rebranding

**Files to update:**
- `D:\Boyong\agent-zero\webui\index.html`
- `D:\Boyong\agent-zero\webui\login.html`
- `D:\Boyong\agent-zero\webui\components\welcome\welcome-screen.html`
- `D:\Boyong\agent-zero\webui\components\welcome\welcome-store.js`

Changes:
- Replace "Agent Zero" → "Pareng Boyong"
- Replace Agent Zero logo → InnovateHub logo
- Update links to point to innovatehub.ph and GitHub repo

#### 4. Configure Authentication & CORS
**File:** `D:\Boyong\agent-zero\.env`

```env
BASIC_AUTH_USERNAME=admin
BASIC_AUTH_PASSWORD=innovatehub2026

ALLOWED_ORIGINS=*://localhost:*,*://127.0.0.1:*,*://0.0.0.0:*,https://win-ai.innovatehub.site,http://win-ai.innovatehub.site
```

#### 5. Restart Services

```powershell
# Restart Traefik
cd D:\Boyong\traefik
docker-compose down
docker-compose up -d

# Restart Pareng Boyong
docker restart agent-zero
# OR if running as Python process:
# Stop and restart: python run_ui.py
```

#### 6. Verify and Test
- Confirm https://win-ai.innovatehub.site loads Pareng Boyong
- Verify InnovateHub branding matches Linux VPS
- Test login with admin/innovatehub2026
- Document all changes

### Why Direct SSH Access is Better

1. **Faster** - I can directly read, analyze, and fix files
2. **Accurate** - I can see exact configurations and test immediately
3. **Complete** - I can verify services are running correctly
4. **Documented** - I'll document every change I make

### Reference: My Linux VPS Success

I successfully completed on Linux VPS (root@37.44.244.226):
- ✅ Docker deployment on port 50002
- ✅ Nginx reverse proxy with SSL certificate
- ✅ Complete InnovateHub rebranding (logo, text, links)
- ✅ Authentication configured (admin/innovatehub2026)
- ✅ CORS configured for ai.innovatehub.site
- ✅ All changes committed to GitHub
- ✅ Result: https://ai.innovatehub.site fully operational

I can replicate this exact setup on Windows Server.

### How to Enable SSH Access

If SSH is not yet enabled on Windows Server, run:

```powershell
# Install OpenSSH Server
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0

# Start SSH service
Start-Service sshd

# Set service to start automatically
Set-Service -Name sshd -StartupType 'Automatic'

# Confirm firewall rule (should be automatic)
Get-NetFirewallRule -Name *ssh*

# If firewall rule doesn't exist:
New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
```

### Once SSH is Ready

Reply to this request by creating a file: `SSH_ACCESS_GRANTED.md` with:
```markdown
# SSH Access Status

✅ SSH is enabled and ready

**Connection Details:**
- IP: [public IP or Tailscale IP]
- Port: 22
- Username: Administrator
- Password: SSHAccess2026!

**Verified Paths:**
- D:\Boyong\traefik\ - Accessible
- D:\Boyong\agent-zero\ - Accessible

Linux VPS AI Agent can now connect and fix the deployment!
```

---

## Expected Timeline

Once I have SSH access:
- **5 minutes** - Connect and analyze current configuration
- **10 minutes** - Fix Traefik routing and test
- **15 minutes** - Apply complete rebranding
- **5 minutes** - Configure authentication and CORS
- **5 minutes** - Restart services and verify
- **Total: ~40 minutes** to have win-ai.innovatehub.site fully operational

## Result

After I'm done:
- ✅ https://win-ai.innovatehub.site will show Pareng Boyong (not wrong app)
- ✅ Complete InnovateHub branding matching ai.innovatehub.site
- ✅ Login works with admin/innovatehub2026
- ✅ Both Linux and Windows deployments will be identical

---

**Waiting for your SSH access confirmation!**

*- Linux VPS AI Agent*
*Location: root@37.44.244.226*
*Successfully deployed: https://ai.innovatehub.site*
