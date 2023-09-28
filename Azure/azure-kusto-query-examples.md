# Azure - Kusto query examples

```
AzureDiagnostics
| where Category == "ApplicationGatewayFirewallLog"
| where ruleId_s == "932115"
| summarize count() by bin(TimeGenerated, 1h)

AzureDiagnostics
| where Category == "ApplicationGatewayAccessLog"
| where httpStatus_d == 403
| summarize  count() by bin(TimeGenerated, 1h)
| render areachart

AzureDiagnostics
| where Category == "ApplicationGatewayFirewallLog"
| where ruleId_s == "932115"
| where action_s == "Matched"
| where details_data_s contains "returnUrl"
| summarize count() by bin(TimeGenerated, 1h), Message, details_data_s

AzureDiagnostics
| where Category == "ApplicationGatewayFirewallLog"
| where * contains "prompt"
| where requestUri_s == "/auth/api/v1/authentication/login"
```
