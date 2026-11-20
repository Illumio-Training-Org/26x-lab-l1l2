---
slug: lab
id: jaaa3auujaqp
type: challenge
title: Illumio Lab Environment
teaser: Access the Illumio Console, then pair workloads, onboard AWS, and connect
  a container cluster
notes:
- type: text
  contents: |-
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&display=swap" rel="stylesheet">
    <style>
      .splash-wrap { font-family: 'Montserrat', sans-serif; color: #d4d4d4; background: #141720; padding: 3% 4% 4% 4%; box-sizing: border-box; width: min(90vw, 1300px); position: relative; left: 50%; transform: translateX(-50%); }
      .splash-logo { width: 444px; max-width: 70%; height: auto; display: block; margin: 0 0 2.2em; }
      .splash-wrap h1 { font-family: 'Montserrat', sans-serif; font-size: 1.6em; font-weight: 700; line-height: 1.25; margin: 0 0 0.8em; white-space: nowrap; }
      .splash-wrap p { margin: 0 0 0.4em; font-size: 1em; }
      .splash-wrap ul { margin: 0 0 1.2em; padding: 0; list-style: none; }
      .splash-wrap li { margin: 0 0 0.35em; font-size: 0.8em; white-space: nowrap; }
      .splash-wrap li::before { content: "- "; }
      .splash-contact { margin: 0 0 1.4em; font-size: 1em; line-height: 1.5; }
      .splash-cta { font-size: 1em; font-weight: 700; }
    </style>
    <div class="splash-wrap">
      <img class="splash-logo" src="../assets/illumio-logo-splash.png" alt="Illumio" />
      <h1>Welcome to your Illumio Training Lab</h1>
      <p>This is your opportunity to:</p>
      <ul>
        <li>Learn how Zero Trust Segmentation protects against breaches</li>
        <li>Discover how Illumio seamlessly integrates with cloud platforms</li>
        <li>Gain actionable strategies to enhance your security posture</li>
        <li>Connect with industry experts and peers in your field</li>
      </ul>
      <div class="splash-contact">
        Illumio Training<br>
        training@illumio.com
      </div>
      <div class="splash-cta">Click &rsaquo; for a short video on using Instruqt</div>
    </div>
- type: video
  url: https://www.youtube.com/embed/_QALLe3DJpk
tabs:
- id: pa1wvxh2tqxs
  title: Illumio & AWS
  type: service
  hostname: cloud-client
  path: /
  port: 80
- id: khmapigezizp
  title: Linux
  type: terminal
  hostname: linux-vm
  cmd: bash
- id: yfupxudcytvz
  title: Windows
  type: terminal
  hostname: windows-vm
- id: rzwkoscq6ssz
  title: CloudCLI
  type: terminal
  hostname: cloud-client
  cmd: bash
- id: muqbadjgv0h6
  title: k3s console
  type: terminal
  hostname: host
  cmd: bash
difficulty: ""
timelimit: 0
enhanced_loading: null
---
🔑 Console
==========

![Illumio](../assets/illumio-logo-banner.png)

**[Click here to open the Illumio Console]([[ Instruqt-Var key="MAGICURL" hostname="cloud-client" ]])**

If the link doesn't open, copy this into a new browser tab:

```
[[ Instruqt-Var key="MAGICURL" hostname="cloud-client" ]]
```

---


🧩 Lab 1
===

_Lab 1 instructions go here._

---

🧩 Lab 2
===

_Lab 2 instructions go here._

---

🧩 Lab 3
===

_Lab 3 instructions go here._

---

🧩 Lab 4
===

_Lab 4 instructions go here._

---

🧩 Lab 5
===

_Lab 5 instructions go here._

---

🛠️ Advanced
===

> [!WARNING]
> These commands are only for use in troubleshooting, if required by the instructor.

Using the CloudCLI Tab

To show all the lab's credentials:

```run
. /root/.pce-sa-key
echo "PCE:                  $AUTOACCOUNT_PCE_FQDN"
echo "Org ID:               $AUTOACCOUNT_ORG_ID"
echo "API key:              api_$AUTOACCOUNT_APIKEY_ID"
echo "API secret:           $AUTOACCOUNT_APIKEY_SECRET"
echo "Service-account key:  $SA_KEY_USER (role $SA_ROLE)"
echo "Service-account secret: $SA_KEY_SECRET"
```

To test the deployment process:

```run
BASE="https://$AUTOACCOUNT_PCE_FQDN/api/v2/orgs/$AUTOACCOUNT_ORG_ID"
AUTH="api_${AUTOACCOUNT_APIKEY_ID}:${AUTOACCOUNT_APIKEY_SECRET}"

count() { curl -s -u "$AUTH" "$BASE$1" | python3 -c "import json,sys; print(len(json.load(sys.stdin)))"; }

echo "Labels:            $(count /labels)"
echo "Label Dimensions:  $(count /label_dimensions)"
echo "Pairing Profiles:  $(count /pairing_profiles)"
echo "Workloads:         $(count /workloads?max_results=1000)"
echo "Services:          $(count /sec_policy/draft/services)"
echo "IP Lists:          $(count /sec_policy/draft/ip_lists)"
echo "User Groups:       $(count /security_principals)"

curl -s -u "$AUTH" "$BASE/sec_policy/draft/rule_sets" | python3 -c "
import json, sys
d = json.load(sys.stdin)
rules = sum(len(r.get('rules', [])) + len(r.get('deny_rules', [])) for r in d)
print(f'Rulesets:          {len(d)}')
print(f'Rules:             {rules}')
"
```
