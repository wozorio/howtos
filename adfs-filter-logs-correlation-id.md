# Filter ADFS logs by Correlation ID

Applying an XML filter on Event Viewer to filter out logs based on a specific Correlation/Activity ID is quite handy when it comes to troubleshooting. Below is an example on how this can be done. 

1. Open Event Viewer, right-click **Debug** under **Applications and Services Logs** and select **Filter Current Log...**

1. Click the XML tab, select the **Edit query manually** checkbox and paste the query below:

```bash
<QueryList>
  <Query Id="0" Path="AD FS Tracing/Debug">
    <Select Path="AD FS/Admin">
      *[System[Correlation[@ActivityID='{217C64D7-7346-4E27-DB07-0080030000BB}']]]
    </Select>
  </Query>
</QueryList>
```
> **NOTE**: Replace the value of the ActivityID with the value of the Correlation/Activity ID you want to investigate.
