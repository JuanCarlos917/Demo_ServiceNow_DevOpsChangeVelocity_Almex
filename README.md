# Almex IT Operations Dashboard

> **Demo**: ServiceNow DevOps Change Velocity × GitHub Actions Integration

This project demonstrates the end-to-end integration between **ServiceNow DevOps Change Velocity** and **GitHub Actions** for automated change management.

## What This Demo Shows

1. **Push code** → GitHub Actions triggers the pipeline
2. **Build & Test** → Automated quality gates
3. **Register Artifact** → ServiceNow tracks the artifact
4. **Deploy to Staging** → No change request needed
5. **Change Request** → ServiceNow automatically creates a CR and **pauses the pipeline**
6. **Approval** → Change Manager approves in ServiceNow
7. **Deploy to Production** → Pipeline resumes after approval

## Pipeline Flow

```
Push to main
    │
    ▼
┌─────────────┐
│  Build &     │
│  Test        │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│  Register    │
│  Artifact    │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│  Deploy to   │
│  Staging     │
└──────┬──────┘
       │
       ▼
┌─────────────────────────────┐
│  ⏸️  ServiceNow Change      │
│     Request Created         │
│     PIPELINE PAUSED         │
│     Awaiting Approval       │
└──────────────┬──────────────┘
               │ ✅ Approved
               ▼
┌─────────────┐
│  Deploy to   │
│  Production  │
└─────────────┘
```

## Setup Requirements

### GitHub Secrets

| Secret | Value |
|--------|-------|
| `SN_INSTANCE_URL` | `https://<instance>.service-now.com` |
| `SN_ORCHESTRATION_TOOL_ID` | Tool sys_id from ServiceNow |
| `SN_DEVOPS_INTEGRATION_TOKEN` | Integration token from ServiceNow |

### ServiceNow

- DevOps Change Velocity installed and configured
- GitHub tool onboarded via DevOps Workspace
- Webhooks configured for this repository

## Tech Stack

- **Frontend**: HTML5, CSS3, Vanilla JS
- **CI/CD**: GitHub Actions
- **Change Management**: ServiceNow DevOps Change Velocity
- **DORA Metrics**: Tracked via ServiceNow DevOps Insights

---

**Built by [Ipsum Technology](https://www.ipsumtechnology.com)** — ServiceNow Elite Partner · Consulting & Implementation
