# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: 06-verify-gateway-tabs.spec.js >> REST API Gateway Tabs >> should show modified badge after editing a persisted route
- Location: tests/06-verify-gateway-tabs.spec.js:992:5

# Error details

```
Error: expect(locator).toHaveCount(expected) failed

Locator:  locator('#endpoint-config').locator('.route-form')
Expected: 0
Received: 1
Timeout:  5000ms

Call log:
  - Expect "toHaveCount" with timeout 5000ms
  - waiting for locator('#endpoint-config').locator('.route-form')
    14 × locator resolved to 1 element
       - unexpected value "1"

```

# Page snapshot

```yaml
- generic [ref=e8]:
  - banner [ref=e9]:
    - generic [ref=e11]:
      - navigation [ref=e12]:
        - generic [ref=e13]:
          - img "NiFi Logo" [ref=e16] [cursor=pointer]
          - generic [ref=e17]:
            - generic [ref=e18]:
              - generic [ref=e19]: testUser
              - generic [ref=e20] [cursor=pointer]: log out
            - button "" [ref=e21]:
              - generic [ref=e23]: 
      - link " Back to Processor" [ref=e26] [cursor=pointer]:
        - /url: "#/process-groups/0fd6d3ec-4be4-5fa7-927c-c5e1c60de0d3/Processor/d9aed3a4-20a8-5cbf-aa19-13400f8890a3"
        - generic [ref=e27]: 
        - text: Back to Processor
  - iframe [active] [ref=e29]:
    - generic [ref=f1e2]:
      - heading "NiFi Component Configuration" [level=1] [ref=f1e3]
      - main [ref=f1e4]:
        - tablist [ref=f1e6]:
          - tab "Endpoint Configuration" [ref=f1e7] [cursor=pointer]
          - tab "Endpoint Tester" [ref=f1e8] [cursor=pointer]
          - tab "Issuer Configuration" [ref=f1e9] [cursor=pointer]
          - tab "Gateway Token Verification" [ref=f1e10] [cursor=pointer]
          - tab "Metrics" [ref=f1e11] [cursor=pointer]
          - tab "Help" [ref=f1e12] [cursor=pointer]
        - generic [ref=f1e13]:
          - tabpanel [ref=f1e14]:
            - generic [ref=f1e15]:
              - heading "Gateway Route Configuration" [level=2] [ref=f1e16]
              - generic [ref=f1e17]:
                - heading "Global Settings" [level=3] [ref=f1e18]
                - table [ref=f1e19]:
                  - rowgroup [ref=f1e20]:
                    - row "Listening Port 9443 Show field help" [ref=f1e21]:
                      - cell "Listening Port" [ref=f1e22]
                      - cell "9443" [ref=f1e23]
                      - cell "Show field help" [ref=f1e24]:
                        - button "Show field help" [ref=f1e25] [cursor=pointer]:
                          - generic [ref=f1e27]: Show field help
                    - row [ref=f1e28]:
                      - cell [ref=f1e29]
                    - row "Max Request Body Size 1.0 MB Show field help" [ref=f1e30]:
                      - cell "Max Request Body Size" [ref=f1e31]
                      - cell "1.0 MB" [ref=f1e32]
                      - cell "Show field help" [ref=f1e33]:
                        - button "Show field help" [ref=f1e34] [cursor=pointer]:
                          - generic [ref=f1e36]: Show field help
                    - row [ref=f1e37]:
                      - cell [ref=f1e38]
                    - row "Queue Size 50 Show field help" [ref=f1e39]:
                      - cell "Queue Size" [ref=f1e40]
                      - cell "50" [ref=f1e41]
                      - cell "Show field help" [ref=f1e42]:
                        - button "Show field help" [ref=f1e43] [cursor=pointer]:
                          - generic [ref=f1e45]: Show field help
                    - row [ref=f1e46]:
                      - cell [ref=f1e47]
                    - row "SSL Enabled Yes Show field help" [ref=f1e48]:
                      - cell "SSL Enabled" [ref=f1e49]
                      - cell "Yes" [ref=f1e50]
                      - cell "Show field help" [ref=f1e51]:
                        - button "Show field help" [ref=f1e52] [cursor=pointer]:
                          - generic [ref=f1e54]: Show field help
                    - row [ref=f1e55]:
                      - cell [ref=f1e56]
                    - row "Listening Host 0.0.0.0 Show field help" [ref=f1e57]:
                      - cell "Listening Host" [ref=f1e58]
                      - cell "0.0.0.0" [ref=f1e59]
                      - cell "Show field help" [ref=f1e60]:
                        - button "Show field help" [ref=f1e61] [cursor=pointer]:
                          - generic [ref=f1e63]: Show field help
                    - row [ref=f1e64]:
                      - cell [ref=f1e65]
              - generic [ref=f1e66]:
                - heading "Standard Endpoints" [level=3] [ref=f1e67]
                - table [ref=f1e68]:
                  - rowgroup [ref=f1e69]:
                    - row "Endpoint Path Methods Enabled Auth Mode Actions" [ref=f1e70]:
                      - columnheader "Endpoint" [ref=f1e71]
                      - columnheader "Path" [ref=f1e72]
                      - columnheader "Methods" [ref=f1e73]
                      - columnheader "Enabled" [ref=f1e74]
                      - columnheader "Auth Mode" [ref=f1e75]
                      - columnheader "Actions" [ref=f1e76]
                  - rowgroup [ref=f1e77]:
                    - row "health /health GET Enabled Local Only, Bearer  Edit" [ref=f1e78]:
                      - cell "health" [ref=f1e79]
                      - cell "/health" [ref=f1e80]
                      - cell "GET" [ref=f1e81]:
                        - generic [ref=f1e82]: GET
                      - cell "Enabled" [ref=f1e83]:
                        - generic [ref=f1e84]: Enabled
                      - cell "Local Only, Bearer" [ref=f1e85]:
                        - generic [ref=f1e86]: Local Only, Bearer
                      - cell " Edit" [ref=f1e87]:
                        - button " Edit" [ref=f1e88] [cursor=pointer]:
                          - generic [ref=f1e89]: 
                          - text: Edit
                    - row "metrics /metrics GET Enabled Local Only, Bearer  Edit" [ref=f1e90]:
                      - cell "metrics" [ref=f1e91]
                      - cell "/metrics" [ref=f1e92]
                      - cell "GET" [ref=f1e93]:
                        - generic [ref=f1e94]: GET
                      - cell "Enabled" [ref=f1e95]:
                        - generic [ref=f1e96]: Enabled
                      - cell "Local Only, Bearer" [ref=f1e97]:
                        - generic [ref=f1e98]: Local Only, Bearer
                      - cell " Edit" [ref=f1e99]:
                        - button " Edit" [ref=f1e100] [cursor=pointer]:
                          - generic [ref=f1e101]: 
                          - text: Edit
                    - 'row "status /status/{traceId} GET Enabled Local Only, Bearer  Edit" [ref=f1e102]':
                      - cell "status" [ref=f1e103]
                      - 'cell "/status/{traceId}" [ref=f1e104]'
                      - cell "GET" [ref=f1e105]:
                        - generic [ref=f1e106]: GET
                      - cell "Enabled" [ref=f1e107]:
                        - generic [ref=f1e108]: Enabled
                      - cell "Local Only, Bearer" [ref=f1e109]:
                        - generic [ref=f1e110]: Local Only, Bearer
                      - cell " Edit" [ref=f1e111]:
                        - button " Edit" [ref=f1e112] [cursor=pointer]:
                          - generic [ref=f1e113]: 
                          - text: Edit
                    - 'row "attachments /attachments/{parentTraceId} POST Enabled Local Only, Bearer  Edit" [ref=f1e114]':
                      - cell "attachments" [ref=f1e115]
                      - 'cell "/attachments/{parentTraceId}" [ref=f1e116]'
                      - cell "POST" [ref=f1e117]:
                        - generic [ref=f1e118]: POST
                      - cell "Enabled" [ref=f1e119]:
                        - generic [ref=f1e120]: Enabled
                      - cell "Local Only, Bearer" [ref=f1e121]:
                        - generic [ref=f1e122]: Local Only, Bearer
                      - cell " Edit" [ref=f1e123]:
                        - button " Edit" [ref=f1e124] [cursor=pointer]:
                          - generic [ref=f1e125]: 
                          - text: Edit
              - alert
              - heading "API Routes" [level=3] [ref=f1e126]
              - generic [ref=f1e127]:
                - table [ref=f1e128]:
                  - rowgroup [ref=f1e129]:
                    - row "Name Connection Path Methods Auth Mode Enabled Actions" [ref=f1e130]:
                      - columnheader "Name" [ref=f1e131]
                      - columnheader "Connection" [ref=f1e132]
                      - columnheader "Path" [ref=f1e133]
                      - columnheader "Methods" [ref=f1e134]
                      - columnheader "Auth Mode" [ref=f1e135]
                      - columnheader "Enabled" [ref=f1e136]
                      - columnheader "Actions" [ref=f1e137]
                  - rowgroup [ref=f1e138]:
                    - row "disabled-test  Config disabled-test /api/disabled GET Bearer Disabled  Edit" [ref=f1e139]:
                      - cell "disabled-test  Config" [ref=f1e140]:
                        - text: disabled-test
                        - generic "Loaded from configuration file (read-only)" [ref=f1e141]:
                          - generic [ref=f1e142]: 
                          - text: Config
                      - cell "disabled-test" [ref=f1e143]
                      - cell "/api/disabled" [ref=f1e144]
                      - cell "GET" [ref=f1e145]:
                        - generic [ref=f1e146]: GET
                      - cell "Bearer" [ref=f1e147]:
                        - generic [ref=f1e148]: Bearer
                      - cell "Disabled" [ref=f1e149]:
                        - generic [ref=f1e150]: Disabled
                      - cell " Edit" [ref=f1e151]:
                        - button " Edit" [ref=f1e152] [cursor=pointer]:
                          - generic [ref=f1e153]: 
                          - text: Edit
                    - row "validated  Config validated /api/validated  Schema POST Bearer Enabled  Edit" [ref=f1e154]:
                      - cell "validated  Config" [ref=f1e155]:
                        - text: validated
                        - generic "Loaded from configuration file (read-only)" [ref=f1e156]:
                          - generic [ref=f1e157]: 
                          - text: Config
                      - cell "validated" [ref=f1e158]
                      - cell "/api/validated  Schema" [ref=f1e159]:
                        - text: /api/validated
                        - generic "JSON Schema validation enabled for request body" [ref=f1e160]:
                          - generic [ref=f1e161]: 
                          - text: Schema
                      - cell "POST" [ref=f1e162]:
                        - generic [ref=f1e163]: POST
                      - cell "Bearer" [ref=f1e164]:
                        - generic [ref=f1e165]: Bearer
                      - cell "Enabled" [ref=f1e166]:
                        - generic [ref=f1e167]: Enabled
                      - cell " Edit" [ref=f1e168]:
                        - button " Edit" [ref=f1e169] [cursor=pointer]:
                          - generic [ref=f1e170]: 
                          - text: Edit
                    - row "data  Config data /api/data  Tracking (POST) GET POST Bearer Enabled  Edit" [ref=f1e171]:
                      - cell "data  Config" [ref=f1e172]:
                        - text: data
                        - generic "Loaded from configuration file (read-only)" [ref=f1e173]:
                          - generic [ref=f1e174]: 
                          - text: Config
                      - cell "data" [ref=f1e175]
                      - cell "/api/data  Tracking (POST)" [ref=f1e176]:
                        - text: /api/data
                        - generic "Async request tracking enabled — POST/PUT/PATCH return 202 with traceId" [ref=f1e177]:
                          - generic [ref=f1e178]: 
                          - text: Tracking (POST)
                      - cell "GET POST" [ref=f1e179]:
                        - generic [ref=f1e180]: GET
                        - generic [ref=f1e181]: POST
                      - cell "Bearer" [ref=f1e182]:
                        - generic [ref=f1e183]: Bearer
                      - cell "Enabled" [ref=f1e184]:
                        - generic [ref=f1e185]: Enabled
                      - cell " Edit" [ref=f1e186]:
                        - button " Edit" [ref=f1e187] [cursor=pointer]:
                          - generic [ref=f1e188]: 
                          - text: Edit
                    - row "upload  Config upload /api/upload  Tracking + Attachments (1-5) (POST) POST Bearer Enabled  Edit" [ref=f1e189]:
                      - cell "upload  Config" [ref=f1e190]:
                        - text: upload
                        - generic "Loaded from configuration file (read-only)" [ref=f1e191]:
                          - generic [ref=f1e192]: 
                          - text: Config
                      - cell "upload" [ref=f1e193]
                      - cell "/api/upload  Tracking + Attachments (1-5) (POST)" [ref=f1e194]:
                        - text: /api/upload
                        - generic "Async request tracking enabled — POST/PUT/PATCH return 202 with traceId" [ref=f1e195]:
                          - generic [ref=f1e196]: 
                          - text: Tracking + Attachments (1-5) (POST)
                      - cell "POST" [ref=f1e197]:
                        - generic [ref=f1e198]: POST
                      - cell "Bearer" [ref=f1e199]:
                        - generic [ref=f1e200]: Bearer
                      - cell "Enabled" [ref=f1e201]:
                        - generic [ref=f1e202]: Enabled
                      - cell " Edit" [ref=f1e203]:
                        - button " Edit" [ref=f1e204] [cursor=pointer]:
                          - generic [ref=f1e205]: 
                          - text: Edit
                    - row "inline-validated  Config inline-validated /api/inline-validated  Schema POST Bearer Enabled  Edit" [ref=f1e206]:
                      - cell "inline-validated  Config" [ref=f1e207]:
                        - text: inline-validated
                        - generic "Loaded from configuration file (read-only)" [ref=f1e208]:
                          - generic [ref=f1e209]: 
                          - text: Config
                      - cell "inline-validated" [ref=f1e210]
                      - cell "/api/inline-validated  Schema" [ref=f1e211]:
                        - text: /api/inline-validated
                        - generic "JSON Schema validation enabled for request body" [ref=f1e212]:
                          - generic [ref=f1e213]: 
                          - text: Schema
                      - cell "POST" [ref=f1e214]:
                        - generic [ref=f1e215]: POST
                      - cell "Bearer" [ref=f1e216]:
                        - generic [ref=f1e217]: Bearer
                      - cell "Enabled" [ref=f1e218]:
                        - generic [ref=f1e219]: Enabled
                      - cell " Edit" [ref=f1e220]:
                        - button " Edit" [ref=f1e221] [cursor=pointer]:
                          - generic [ref=f1e222]: 
                          - text: Edit
                    - row "admin  Config admin /api/admin GET Bearer Enabled  Edit" [ref=f1e223]:
                      - cell "admin  Config" [ref=f1e224]:
                        - text: admin
                        - generic "Loaded from configuration file (read-only)" [ref=f1e225]:
                          - generic [ref=f1e226]: 
                          - text: Config
                      - cell "admin" [ref=f1e227]
                      - cell "/api/admin" [ref=f1e228]
                      - cell "GET" [ref=f1e229]:
                        - generic [ref=f1e230]: GET
                      - cell "Bearer" [ref=f1e231]:
                        - generic [ref=f1e232]: Bearer
                      - cell "Enabled" [ref=f1e233]:
                        - generic [ref=f1e234]: Enabled
                      - cell " Edit" [ref=f1e235]:
                        - button " Edit" [ref=f1e236] [cursor=pointer]:
                          - generic [ref=f1e237]: 
                          - text: Edit
                    - 'row "items  Config items /api/items/{itemId} GET Bearer Enabled  Edit" [ref=f1e238]':
                      - cell "items  Config" [ref=f1e239]:
                        - text: items
                        - generic "Loaded from configuration file (read-only)" [ref=f1e240]:
                          - generic [ref=f1e241]: 
                          - text: Config
                      - cell "items" [ref=f1e242]
                      - 'cell "/api/items/{itemId}" [ref=f1e243]'
                      - cell "GET" [ref=f1e244]:
                        - generic [ref=f1e245]: GET
                      - cell "Bearer" [ref=f1e246]:
                        - generic [ref=f1e247]: Bearer
                      - cell "Enabled" [ref=f1e248]:
                        - generic [ref=f1e249]: Enabled
                      - cell " Edit" [ref=f1e250]:
                        - button " Edit" [ref=f1e251] [cursor=pointer]:
                          - generic [ref=f1e252]: 
                          - text: Edit
                - generic [ref=f1e253]:
                  - generic [ref=f1e254]:
                    - generic [ref=f1e255]:
                      - text: "Route Name:"
                      - button "Show field help" [ref=f1e256] [cursor=pointer]:
                        - generic [ref=f1e258]: Show field help
                    - textbox "Route Name" [ref=f1e259]:
                      - /placeholder: e.g., health-check
                      - text: e2e-modify-test
                    - generic [ref=f1e260]:
                      - checkbox "Route Enabled" [checked] [ref=f1e261]
                      - text: Enabled
                      - button "Show field help" [ref=f1e262] [cursor=pointer]:
                        - generic [ref=f1e264]: Show field help
                  - group "Basic" [ref=f1e265]:
                    - generic [ref=f1e266]: Basic
                    - generic [ref=f1e267]:
                      - generic [ref=f1e268]:
                        - generic [ref=f1e269]:
                          - text: "Path:"
                          - button "Show field help" [ref=f1e270] [cursor=pointer]:
                            - generic [ref=f1e272]: Show field help
                        - textbox "Path" [ref=f1e273]:
                          - /placeholder: /api/resource (required)
                          - text: /api/e2e-modify-test
                      - generic [ref=f1e274]:
                        - generic [ref=f1e275]: "Methods:"
                        - generic [ref=f1e276]:
                          - generic [ref=f1e278]:
                            - text: GET
                            - button "Remove GET" [ref=f1e279] [cursor=pointer]: ×
                          - combobox "Add HTTP method" [ref=f1e281]
                  - group "Authentication" [ref=f1e282]:
                    - generic [ref=f1e283]: Authentication
                    - generic [ref=f1e284]:
                      - generic [ref=f1e285]:
                        - generic [ref=f1e286]:
                          - text: "Auth Mode:"
                          - button "Show field help" [ref=f1e287] [cursor=pointer]:
                            - generic [ref=f1e289]: Show field help
                        - generic [ref=f1e290]:
                          - generic [ref=f1e292]:
                            - text: Bearer
                            - button "Remove Bearer" [ref=f1e293] [cursor=pointer]: ×
                          - combobox "Add auth mode" [ref=f1e295]
                      - generic [ref=f1e296]:
                        - generic [ref=f1e297]:
                          - text: "Required Roles:"
                          - button "Show field help" [ref=f1e298] [cursor=pointer]:
                            - generic [ref=f1e300]: Show field help
                        - textbox "Required Roles" [ref=f1e301]:
                          - /placeholder: admin,user (comma-separated, optional)
                      - generic [ref=f1e302]:
                        - generic [ref=f1e303]:
                          - text: "Required Scopes:"
                          - button "Show field help" [ref=f1e304] [cursor=pointer]:
                            - generic [ref=f1e306]: Show field help
                        - textbox "Required Scopes" [ref=f1e307]:
                          - /placeholder: read,write (comma-separated, optional)
                  - group "Tracking" [ref=f1e308]:
                    - generic [ref=f1e309]: Tracking
                    - generic [ref=f1e311]:
                      - text: Tracking Mode
                      - combobox "Tracking Mode" [ref=f1e312]:
                        - option "None" [selected]
                        - option "Simple (Status)"
                        - option "Attachments"
                      - button "Show field help" [ref=f1e313] [cursor=pointer]:
                        - generic [ref=f1e315]: Show field help
                  - group "Advanced" [ref=f1e316]:
                    - generic [ref=f1e317]: Advanced
                    - generic [ref=f1e319]:
                      - generic [ref=f1e320]: "Max Request Size:"
                      - textbox "Max Request Size" [ref=f1e321]:
                        - /placeholder: Leave empty for global default
                    - generic [ref=f1e323] [cursor=pointer]:
                      - checkbox "Create FlowFile" [checked] [ref=f1e324]
                      - text: Create FlowFile
                      - button "Show field help" [ref=f1e325]:
                        - generic [ref=f1e327]: Show field help
                    - generic [ref=f1e328]:
                      - generic [ref=f1e329]:
                        - text: "NiFi Connection Name:"
                        - button "Show field help" [ref=f1e330] [cursor=pointer]:
                          - generic [ref=f1e332]: Show field help
                      - combobox "NiFi Connection Name" [ref=f1e333]: e2e-modify-test
                    - generic [ref=f1e335] [cursor=pointer]:
                      - checkbox "Enable Schema Validation" [ref=f1e336]
                      - text: Schema Validation
                      - button "Show field help" [ref=f1e337]:
                        - generic [ref=f1e339]: Show field help
                  - alert [ref=f1e340]:
                    - alert [ref=f1e341]:
                      - text: ⚠️
                      - generic [ref=f1e342]:
                        - strong [ref=f1e343]: "Error:"
                        - text: Cannot modify configuration of RestApiGatewayProcessor[id=d9aed3a4-20a8-5cbf-aa19-13400f8890a3] while the Processor is running
                  - generic [ref=f1e344]:
                    - button " Save Route" [active] [ref=f1e345] [cursor=pointer]:
                      - generic [ref=f1e346]: 
                      - text: Save Route
                    - button " Cancel" [ref=f1e347] [cursor=pointer]:
                      - generic [ref=f1e348]: 
                      - text: Cancel
              - button " Add Route" [ref=f1e349] [cursor=pointer]:
                - generic [ref=f1e350]: 
                - text: Add Route
              - group [ref=f1e352]:
                - generic "NiFi Connections (9 relationships)" [ref=f1e353] [cursor=pointer]: NiFi Connections (9 relationships)
              - group [ref=f1e355]:
                - generic "Export Properties" [ref=f1e356] [cursor=pointer]: Export Properties
                - generic [ref=f1e358]:
                  - textbox [ref=f1e359]: "restapi.disabled-test.path = /api/disabled restapi.disabled-test.methods = GET restapi.disabled-test.enabled = false restapi.disabled-test.success-outcome = disabled-test restapi.validated.path = /api/validated restapi.validated.methods = POST restapi.validated.success-outcome = validated restapi.validated.schema = <see processor properties> restapi.data.path = /api/data restapi.data.methods = GET,POST restapi.data.success-outcome = data restapi.data.tracking-mode = simple restapi.upload.path = /api/upload restapi.upload.methods = POST restapi.upload.success-outcome = upload restapi.upload.tracking-mode = attachments restapi.upload.attachments-min-count = 1 restapi.upload.attachments-max-count = 5 restapi.upload.attachments-timeout = 60 sec restapi.inline-validated.path = /api/inline-validated restapi.inline-validated.methods = POST restapi.inline-validated.success-outcome = inline-validated restapi.inline-validated.schema = <see processor properties> restapi.admin.path = /api/admin restapi.admin.methods = GET restapi.admin.required-roles = ADMIN restapi.admin.success-outcome = admin restapi.items.path = /api/items/{itemId} restapi.items.methods = GET restapi.items.success-outcome = items restapi.e2e-modify-test.path = /api/e2e-modify-test restapi.e2e-modify-test.methods = GET restapi.e2e-modify-test.success-outcome = e2e-modify-test"
                  - button "Copy to Clipboard" [ref=f1e360] [cursor=pointer]: Copy to Clipboard
          - text:                   
```

# Test source

```ts
  943  | 
  944  |         // Serial-block hygiene: ensure no route form was left open by a prior test, so the
  945  |         // post-save toHaveCount(0) assertion below reflects only this test's own form.
  946  |         const leftoverForm = endpointConfigPanel.locator(".route-form");
  947  |         if ((await leftoverForm.count()) > 0) {
  948  |             await leftoverForm.first().locator("button", { hasText: "Cancel" }).click().catch(() => {});
  949  |             await expect(leftoverForm).toHaveCount(0, { timeout: 5000 }).catch(() => {});
  950  |         }
  951  | 
  952  |         // Idempotency guard: a route named "e2e-origin-test" must not already
  953  |         // exist (a prior interrupted run would otherwise trigger a duplicate-name
  954  |         // validation error). Remove any leftover before adding (M22).
  955  |         await removeRouteIfPresent(customUIFrame, summaryTable, "e2e-origin-test");
  956  | 
  957  |         // Click Add Route
  958  |         const addRouteBtn = endpointConfigPanel.locator(".add-route-button");
  959  |         await addRouteBtn.click();
  960  | 
  961  |         const routeForm = endpointConfigPanel.locator(".route-form");
  962  |         await expect(routeForm).toBeVisible({ timeout: 5000 });
  963  | 
  964  |         // Fill in new route details
  965  |         const routeName = routeForm.locator(".route-name");
  966  |         await routeName.fill("e2e-origin-test");
  967  |         const pathField = routeForm.locator(".field-path");
  968  |         await pathField.fill("/api/e2e-origin-test");
  969  |         // Select GET via the method chip input
  970  |         const methodInput = routeForm.locator(".method-chip-text-input");
  971  |         await methodInput.fill("GET");
  972  |         await methodInput.press("Enter");
  973  | 
  974  |         // Save
  975  |         const saveBtn = routeForm.locator(".save-route-button");
  976  |         await saveBtn.click();
  977  |         await expect(routeForm).toHaveCount(0, { timeout: 5000 });
  978  | 
  979  |         // Verify the new row was persisted (saved via API with componentId)
  980  |         const newRow = summaryTable.locator(
  981  |             'tr[data-route-name="e2e-origin-test"]',
  982  |         );
  983  |         await expect(newRow).toBeVisible({ timeout: 5000 });
  984  |         await expect(newRow).toHaveAttribute("data-origin", "persisted");
  985  | 
  986  |         // Clean up: remove the route we added so a re-run leaves no residual
  987  |         // "e2e-origin-test" state (M22).
  988  |         await removeRouteIfPresent(customUIFrame, summaryTable, "e2e-origin-test");
  989  |         await expect(newRow).toHaveCount(0, { timeout: 5000 });
  990  |     });
  991  | 
  992  |     test("should show modified badge after editing a persisted route", async ({
  993  |         customUIFrame,
  994  |     }) => {
  995  |         // Navigate to Endpoint Configuration tab
  996  |         const endpointConfigTab = customUIFrame.locator(
  997  |             'a[href="#endpoint-config"]',
  998  |         );
  999  |         await expect(endpointConfigTab).toBeVisible({ timeout: 5000 });
  1000 |         await endpointConfigTab.click();
  1001 | 
  1002 |         const endpointConfigPanel = customUIFrame.locator("#endpoint-config");
  1003 |         await expect(endpointConfigPanel).toBeVisible({ timeout: 5000 });
  1004 | 
  1005 |         // Wait for summary table
  1006 |         const summaryTable = endpointConfigPanel.locator(".route-summary-table");
  1007 |         await expect(summaryTable).toBeVisible({ timeout: 15000 });
  1008 | 
  1009 |         // Self-contained: this test edits a *persisted* route, but the deployment ships only
  1010 |         // built-in (external) routes by default. Create our own persisted route to edit rather
  1011 |         // than depending on one left behind by an earlier serial-block test.
  1012 |         const MODIFY_ROUTE = "e2e-modify-test";
  1013 |         await removeRouteIfPresent(customUIFrame, summaryTable, MODIFY_ROUTE);
  1014 |         const addRouteBtn = endpointConfigPanel.locator(".add-route-button");
  1015 |         await addRouteBtn.click();
  1016 |         const addForm = endpointConfigPanel.locator(".route-form");
  1017 |         await expect(addForm).toBeVisible({ timeout: 5000 });
  1018 |         await addForm.locator(".route-name").fill(MODIFY_ROUTE);
  1019 |         await addForm.locator(".field-path").fill("/api/e2e-modify-test");
  1020 |         const addMethod = addForm.locator(".method-chip-text-input");
  1021 |         await addMethod.fill("GET");
  1022 |         await addMethod.press("Enter");
  1023 |         await addForm.locator(".save-route-button").click();
  1024 |         await expect(addForm).toHaveCount(0, { timeout: 5000 });
  1025 | 
  1026 |         // Locate the freshly-persisted route and capture its name for re-location after save.
  1027 |         const firstPersistedRow = summaryTable.locator(
  1028 |             `tbody tr[data-route-name="${MODIFY_ROUTE}"]`,
  1029 |         );
  1030 |         await expect(firstPersistedRow).toBeVisible({ timeout: 5000 });
  1031 |         const routeName = MODIFY_ROUTE;
  1032 | 
  1033 |         // Click Edit
  1034 |         const editBtn = firstPersistedRow.locator(".edit-route-button");
  1035 |         await editBtn.click();
  1036 | 
  1037 |         const routeForm = endpointConfigPanel.locator(".route-form");
  1038 |         await expect(routeForm).toBeVisible({ timeout: 5000 });
  1039 | 
  1040 |         // Save without changing anything — the act of saving marks it modified
  1041 |         const saveBtn = routeForm.locator(".save-route-button");
  1042 |         await saveBtn.click();
> 1043 |         await expect(routeForm).toHaveCount(0, { timeout: 5000 });
       |                                 ^ Error: expect(locator).toHaveCount(expected) failed
  1044 | 
  1045 |         // Re-locate row by name — origin stays persisted after save with componentId
  1046 |         const savedRow = summaryTable.locator(
  1047 |             `tbody tr[data-route-name="${routeName}"]`,
  1048 |         );
  1049 |         await expect(savedRow).toHaveAttribute("data-origin", "persisted");
  1050 |         // No end-cleanup: a just-edited ("modified") route's delete is handled differently by
  1051 |         // the UI; the idempotent removeRouteIfPresent at the top of this test removes any
  1052 |         // leftover e2e-modify-test on the next run, so residual state cannot accumulate.
  1053 |     });
  1054 | 
  1055 |     test("should display endpoint tester with route selector and controls", async ({
  1056 |         customUIFrame,
  1057 |         processorService,
  1058 |     }) => {
  1059 |         // Navigate to Endpoint Tester tab
  1060 |         await processorService.clickTab(customUIFrame, "Endpoint Tester");
  1061 | 
  1062 |         // Verify the endpoint tester panel is visible
  1063 |         const endpointTesterPanel = customUIFrame.locator("#endpoint-tester");
  1064 |         await expect(endpointTesterPanel).toBeVisible({ timeout: 5000 });
  1065 | 
  1066 |         // Verify route selector exists
  1067 |         const routeSelector = endpointTesterPanel.locator(".route-selector");
  1068 |         await expect(routeSelector).toBeVisible({ timeout: 5000 });
  1069 | 
  1070 |         // Verify method selector exists
  1071 |         const methodSelector = endpointTesterPanel.locator(".method-selector");
  1072 |         await expect(methodSelector).toBeVisible({ timeout: 5000 });
  1073 | 
  1074 |         // Verify token input exists
  1075 |         const tokenInput = endpointTesterPanel.locator(".token-input");
  1076 |         await expect(tokenInput).toBeVisible({ timeout: 5000 });
  1077 | 
  1078 |         // Verify send request button exists
  1079 |         const sendButton = endpointTesterPanel.locator(".send-request-button");
  1080 |         await expect(sendButton).toBeVisible({ timeout: 5000 });
  1081 | 
  1082 |         // Response display should be initially hidden
  1083 |         const responseDisplay = endpointTesterPanel.locator(".response-display");
  1084 |         await expect(responseDisplay).toBeHidden();
  1085 |     });
  1086 | 
  1087 |     test("should send request via endpoint tester and display response", async ({
  1088 |         customUIFrame,
  1089 |         processorService,
  1090 |     }) => {
  1091 |         // Navigate to Endpoint Tester tab
  1092 |         await processorService.clickTab(customUIFrame, "Endpoint Tester");
  1093 | 
  1094 |         const endpointTesterPanel = customUIFrame.locator("#endpoint-tester");
  1095 |         await expect(endpointTesterPanel).toBeVisible({ timeout: 5000 });
  1096 | 
  1097 |         // Fill in the token input with a valid Keycloak token
  1098 |         const tokenInput = endpointTesterPanel.locator(".token-input");
  1099 |         await expect(tokenInput).toBeVisible({ timeout: 5000 });
  1100 |         const validToken = await getValidAccessToken();
  1101 |         await tokenInput.fill(validToken);
  1102 | 
  1103 |         // Click Send Request
  1104 |         const sendButton = endpointTesterPanel.locator(".send-request-button");
  1105 |         await expect(sendButton).toBeVisible({ timeout: 5000 });
  1106 |         await sendButton.click();
  1107 | 
  1108 |         // Wait for response display to appear
  1109 |         const responseDisplay = endpointTesterPanel.locator(".response-display");
  1110 |         await expect(responseDisplay).toBeVisible({ timeout: 30000 });
  1111 | 
  1112 |         const responseText = await responseDisplay.textContent();
  1113 | 
  1114 |         // Must not be an auth/CSRF infrastructure error
  1115 |         assertNoAuthError(responseText);
  1116 | 
  1117 |         // Response should contain HTTP status information
  1118 |         expect(responseText).toMatch(/\d{3}|status|response/i);
  1119 |     });
  1120 | 
  1121 |     test("should send POST request with body via endpoint tester", async ({
  1122 |         customUIFrame,
  1123 |         processorService,
  1124 |     }) => {
  1125 |         // Navigate to Endpoint Tester tab
  1126 |         await processorService.clickTab(customUIFrame, "Endpoint Tester");
  1127 | 
  1128 |         const endpointTesterPanel = customUIFrame.locator("#endpoint-tester");
  1129 |         await expect(endpointTesterPanel).toBeVisible({ timeout: 5000 });
  1130 | 
  1131 |         // Select a route that supports POST (route order is non-deterministic)
  1132 |         const routeSelector = endpointTesterPanel.locator(".route-selector");
  1133 |         await routeSelector.selectOption("/api/data");
  1134 | 
  1135 |         // Select POST method (now guaranteed to be available for this route)
  1136 |         const methodSelector = endpointTesterPanel.locator(".method-selector");
  1137 |         await methodSelector.selectOption("POST");
  1138 | 
  1139 |         // Verify body textarea becomes visible
  1140 |         const bodyGroup = endpointTesterPanel.locator(".body-group");
  1141 |         await expect(bodyGroup).toBeVisible({ timeout: 5000 });
  1142 | 
  1143 |         const bodyInput = endpointTesterPanel.locator(".body-input");
```