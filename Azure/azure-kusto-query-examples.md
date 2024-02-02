# Azure - Kusto query examples

# Application Gateway (WAF)

## Determine blocked requests by OWASP rule and the blocking reason

```
AzureDiagnostics
| where Category == "ApplicationGatewayFirewallLog"
| where action_s == "Matched"
| project
    TimeGenerated,
    ruleId_s,
    details_message_s,
    requestUri_s,
    details_data_s,
    transactionId_g
| join AzureDiagnostics on transactionId_g
| where action_s == "Blocked"
| where details_data_s contains "REQUEST_COOKIES:" or details_data_s contains "ARGS:"
| extend args = split(details_data_s, "ARGS:")[1]
| extend BlockedArgs = split(args, ":")[0]
| extend BlockedArgsName = split(BlockedArgs, "=")[0]
| extend url = split(requestUri_s, "?")[0]
| extend isCookie = split(details_data_s, "REQUEST_COOKIES:")[1]
| extend BlockedCookie = split(isCookie, ":")[0]
| extend BlockReason = strcat(BlockedArgsName, BlockedCookie)
```

# Application Insights

## Identify requests by client failing due to invalid or expired refresh tokens

```
traces
| where * contains "Refresh token validation failed"
| extend ClientId = extract(@"ClientId"":""([^""]+)", 1, message)
| summarize count() by bin(timestamp, 1h), tostring(ClientId)
| render timechart with (title = "Refresh Token Validation Failed by ClientId")
| order by ClientId desc
```
