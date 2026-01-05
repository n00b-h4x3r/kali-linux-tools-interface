# Next Steps: BlackArch Tools Interface

## ✅ Completed
- [x] Database name changed from `kali` to `blackarch`
- [x] All branding updated (titles, headers, footers)
- [x] Tool URLs updated to BlackArch references
- [x] Hardcoded paths removed (using system binaries)
- [x] Documentation updated (README, gitbook files)
- [x] Installation instructions updated for Arch Linux

## 🔧 Immediate Fixes Needed

### 1. Fix Remaining Hardcoded Path
- **Issue**: One tool still has a hardcoded path
- **Status**: ✅ Fixed - `theharvester` now uses system binary

### 2. Test Database Import
```bash
# Create the database
mysql -u root -p -e "CREATE DATABASE blackarch;"

# Import the schema
mysql -u root -p blackarch < assets/database.sql
```

### 3. Verify Configuration
- Check `assets/includes/config.php` - ensure database credentials are correct
- Test SSH connection settings if using remote execution

## 🚀 Recommended Next Steps

### Priority 1: Expand Tool Database
**Current**: ~12 tools  
**Target**: Add popular BlackArch tools

**Popular BlackArch Tools to Add:**
- **Reconnaissance**: `recon-ng`, `maltego`, `spiderfoot`, `osrframework`
- **Web Application**: `sqlmap`, `burpsuite`, `nikto`, `dirb`, `gobuster`
- **Exploitation**: `metasploit`, `exploitdb`, `searchsploit`
- **Password Cracking**: `john`, `hashcat`, `hydra`, `medusa`
- **Wireless**: `wifite`, `reaver`, `aircrack-ng`, `kismet`
- **Forensics**: `volatility`, `autopsy`, `sleuthkit`
- **Reverse Engineering**: `ghidra`, `radare2`, `cutter`
- **Sniffing**: `wireshark`, `tcpdump`, `ettercap`

**How to Add Tools:**
1. Install tool on BlackArch: `sudo pacman -S <tool-name>`
2. Find the command: `which <tool-name>` or `pacman -Ql <tool-name> | grep bin`
3. Add to database using the `tools` table structure
4. Add command options to `commands` table if needed

### Priority 2: Expand Tool Categories
**Current Categories** (only 5 active):
- Information Gathering
- Password Attacks  
- Sniffing & Spoofing
- Vulnerability Analysis
- Web Applications

**BlackArch Categories to Add:**
- Anti-forensic
- Automation
- Backdoor
- Binary
- Blacklist
- Bluetooth
- Code-audit
- Cracker
- Crypto
- Database
- Debugger
- Decompiler
- Defensive
- Disassembler
- Dos
- Exploitation
- Fingerprint
- Firewall
- Forensic
- Fuzzer
- Hardware
- Honeypot
- Keylogger
- Malware
- Mobile
- Net
- Network
- Packer
- Proxy
- Radio
- Recon
- Reversing
- Scanner
- Sniffer
- Social
- Spoof
- Tunnel
- Unpacker
- Voip
- Webapp
- Wireless

**Update**: `assets/includes/tools-categories.php` to enable more filter buttons

### Priority 3: Create Tool Import Script
Create a PHP script to help import tools from BlackArch repository:

```php
// Example: import-tools.php
// Script to parse BlackArch tool list and add to database
// Could fetch from: https://blackarch.org/tools.html
```

### Priority 4: Update UI for BlackArch Theme
- Consider adding BlackArch logo/branding
- Update color scheme to match BlackArch (black/red theme)
- Add tool count badge showing "2,800+ tools available"

### Priority 5: Add Tool Search Functionality
- Implement search bar in `tools-list.php`
- Filter by category, name, or description
- Add pagination for large tool lists

### Priority 6: Create Installation Guide
Create `INSTALL.md` with:
- BlackArch installation steps
- Repository setup instructions
- Tool installation examples
- Database setup guide
- Troubleshooting section

### Priority 7: Add Tool Management Interface
Create admin pages for:
- Adding new tools via web interface
- Editing tool commands
- Managing tool categories
- Bulk import from BlackArch repository

## 📋 Database Schema Notes

### Tools Table Structure
```sql
- id: Auto-increment primary key
- name: Tool short name
- fullname: Full tool name
- categories: CSS filter classes (space-separated)
- description: URL to tool description
- site: Official website
- github: GitHub repository URL
- released: 'Yes' or NULL
- avatar: Image path
- cmd: Command to execute
- target: Target parameter flag (e.g., '-d', '--url')
- resume: Tool description text
- category: Primary category
- category2: Secondary category
- solution: HTML solution/remediation text
```

### Commands Table Structure
```sql
- id: Auto-increment primary key
- name: Command option name
- description: Description text
- examples: Example usage
- tool: Foreign key to tools.id
- type: 'input', 'checkbox', 'target', 'show'
- command: Command flag/option
- example: Example value
- sudo: 1 if requires sudo, NULL otherwise
- category: Command category grouping
```

## 🧪 Testing Checklist

- [ ] Database imports successfully
- [ ] Tools list displays correctly
- [ ] Tool execution works via SSH
- [ ] Reports save correctly
- [ ] Terminal integration works
- [ ] All tool commands execute properly
- [ ] Category filters work
- [ ] Search functionality (if added)

## 📚 Resources

- **BlackArch Tools**: https://blackarch.org/tools.html
- **BlackArch Guide**: https://blackarch.org/guide.pdf
- **BlackArch GitHub**: https://github.com/BlackArch/blackarch
- **Arch Linux Wiki**: https://wiki.archlinux.org/
- **pacman Documentation**: https://wiki.archlinux.org/title/Pacman

## 🎯 Quick Wins

1. **Add 10 most popular tools** (sqlmap, metasploit, burpsuite, etc.)
2. **Enable all category filters** in tools-categories.php
3. **Add search functionality** to tools-list.php
4. **Create tool import template** for easy additions
5. **Update README** with BlackArch-specific examples

---

**Note**: The current database has only ~12 tools. BlackArch has 2,800+ tools available. Start by adding the most commonly used tools, then gradually expand based on user needs.

