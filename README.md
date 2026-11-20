# ! 26.x Lab COPY For L1/L2 Prep

I made this as a standalone copy of the `! 26.x Lab` Instruqt track (track ID `ojcwc1hueyms`, slug `26x-lab-copy`) for L1/L2 prep. It builds everything the main lab builds — the Illumio PCE org and magic link, AWS environment, Linux and Windows VMs, k3s/Cilium cluster, and Project Crystal traffic — but the lab instructions have been removed, leaving empty sections Lab 1 to Lab 5 for you to fill in.

It is fully independent of the main 26.x course: nothing here is cloned from the `26x-course` repo or from anyone's personal GitHub account.

## What's in this repo

| Folder | Purpose |
|---|---|
| `Lab/` | The Instruqt track itself (`track.yml`, `config.yml`, challenges, scripts) |
| `terraform-lab/` | The AWS build the lab runs at boot (4 EC2s, VPC, subnets) |
| `dependencies/illumio-instruqt-terraform-template/` | The Illumio & AWS landing-page tile template |
| `dependencies/pc-connector/` | Terraform module that creates the Project Crystal deployment |

The lab's setup scripts clone **this repo** (`Illumio-Training-Org/26x-lab-l1l2`) when each sandbox boots, so the repo must stay **public** and these folder names must not change.

## Editing

You can edit the track directly in Instruqt. To keep this repo in step, either link it with Instruqt's GitHub integration, or run `instruqt track pull` from inside `Lab/` and commit.

Changes to `terraform-lab/` or `dependencies/` take effect for every new session as soon as they are pushed to `main`.
