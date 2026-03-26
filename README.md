# @hasna/analytics

Business analytics for AI agents — track KPIs, manage dashboards, generate reports, and get AI-powered executive summaries.

## Install

```bash
npm install -g @hasna/analytics
```

## CLI

```bash
# KPIs
analytics kpi record --name revenue --value 50000 --category Finance --period 2024-Q1
analytics kpi get revenue
analytics kpi trend revenue --days 30
analytics kpi list --category Finance --latest

# Dashboards
analytics dashboard create --name "Sales Overview" --description "Main sales dashboard"
analytics dashboard list
analytics dashboard get <id>
analytics dashboard update <id> --name "Updated Name"
analytics dashboard delete <id>

# Reports
analytics report generate --name "Q1 Review" --type quarterly --period 2024-Q1
analytics report list --type quarterly
analytics report get <id>

# Health & Summary
analytics health
analytics summary
```

## MCP Server

```bash
analytics-mcp
```

Add to your MCP config:

```json
{
  "mcpServers": {
    "analytics": {
      "command": "analytics-mcp"
    }
  }
}
```

### MCP Tools

| Tool | Description |
|------|-------------|
| `record_kpi` | Record a KPI value |
| `get_kpi` | Get latest value for a KPI by name |
| `get_kpi_trend` | Get KPI trend over N days |
| `list_kpis` | List KPIs with optional filters |
| `get_latest_kpis` | Most recent value per unique KPI |
| `delete_kpi` | Delete a KPI entry |
| `create_dashboard` | Create a dashboard |
| `get_dashboard` | Get a dashboard by ID |
| `list_dashboards` | List all dashboards |
| `update_dashboard` | Update a dashboard |
| `delete_dashboard` | Delete a dashboard |
| `generate_report` | Generate a business report |
| `get_report` | Get a report by ID |
| `list_reports` | List reports with filters |
| `delete_report` | Delete a report |
| `get_business_health` | Get health summary across all KPIs |
| `generate_executive_summary` | AI-powered executive summary |

## Data Storage

Data is stored in `~/.hasna/analytics/analytics.db` by default.

Override with env vars:
- `HASNA_ANALYTICS_DIR` — full path to directory
- `ANALYTICS_DIR` — full path to directory

## Programmatic API

```typescript
import { recordKpi, getKpi, getBusinessHealth } from "@hasna/analytics";

const kpi = recordKpi({ name: "revenue", value: 50000, category: "Finance" });
const health = getBusinessHealth();
```

## License

Apache-2.0
