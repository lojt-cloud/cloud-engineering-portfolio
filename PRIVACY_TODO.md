# Privacy To-Do (cover before going public)

## ✅ Resolved
- [x] Personal Gmail address (was visible in git config screenshot) — covered.
- [x] System Information window — device name "LOJTLAPTOP", Dell service
      tag/SKU — covered.
- [x] EC2_Deployment_Report.md — public IP, private IP, instance ID, public
      DNS, private DNS, and MAC address all replaced with `<placeholder>`
      values. Windows username removed from file paths (now uses `~/`).
- [x] EC2_Deployment_Report.pdf — removed entirely (was a duplicate of the
      .md in a harder-to-edit format; .md is now the sole, cleaned version).

## ⬜ Still open — screenshots only
The text-based redaction above does NOT cover screenshots — these still
show the real values and need manual blurring or a re-shoot:
- [ ] `ssh-successful-connection-banner.png` — shows full SSH command with
      real public IP and `/c/Users/lojtb/...` path (Windows username visible).
- [ ] `ssh-session-full-console.png` — same issue, same command visible.
- [ ] `chmod_400.png` — shows `/c/Users/lojtb/...` path (no IP, just username).
- [ ] `aws-ec2-instance-summary.png` — shows VPC ID, Instance ID, Public IP,
      Public DNS in plain text (account alias is cropped out of frame in
      the current version, so that part's fine by accident).

## Standing rule going forward
- [ ] Use `~/` instead of full `/c/Users/<name>/...` paths in any command
      that might get screenshotted — avoids leaking the Windows username at
      the source instead of fixing it after the fact.
- [ ] Before flipping ANY repo public, re-check new screenshots for: account
      aliases/usernames, real IPs, personal email, device names — see
      `BEFORE_GOING_PUBLIC.md` for the full checklist.
- [ ] Lower urgency: once the EC2 instance is terminated, its IP/instance ID
      become historical and harmless even if a screenshot still shows them —
      but the Windows username persists regardless, so that one's worth
      fixing at the source (see rule above).
