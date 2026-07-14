# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: 01-verify-configuration-tab.spec.js >> Configuration Tab >> should delete an existing issuer
- Location: tests/01-verify-configuration-tab.spec.js:171:5

# Error details

```
Error: Timeout 10000ms exceeded while waiting on the predicate
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
        - /url: "#/process-groups/bfbfae55-79b0-5ac6-9830-8a95a2230479/Processor/143914df-0581-5ae2-ab51-514a7bc830e6"
        - generic [ref=e27]: 
        - text: Back to Processor
  - iframe [active] [ref=e29]:
    - generic [ref=f1e2]:
      - heading "NiFi Component Configuration" [level=1] [ref=f1e3]
      - main [ref=f1e4]:
        - tablist [ref=f1e6]:
          - tab "Configuration" [ref=f1e7] [cursor=pointer]
          - tab "Token Verification" [ref=f1e8] [cursor=pointer]
          - tab "Metrics" [ref=f1e9] [cursor=pointer]
          - tab "Help" [ref=f1e10] [cursor=pointer]
        - generic [ref=f1e11]:
          - tabpanel [ref=f1e12]:
            - generic [ref=f1e13]:
              - heading "Issuer Configurations" [level=2] [ref=f1e14]
              - paragraph [ref=f1e15]: Configure JWT issuers for token validation. Each issuer requires a name and properties like jwks-url and issuer URI.
              - alert
              - button " Add Issuer" [ref=f1e16] [cursor=pointer]:
                - generic [ref=f1e17]: 
                - text: Add Issuer
          - text:              
```

# Test source

```ts
  142 |         // the live processor (N67).
  143 |         const allForms = customUIFrame.locator(".issuer-form");
  144 |         const confirmButton = customUIFrame
  145 |             .locator(
  146 |                 '.confirmation-dialog .confirm-button, button:has-text("Confirm"), button:has-text("Yes")',
  147 |             )
  148 |             .first();
  149 |         const formCount = await allForms.count();
  150 |         for (let i = formCount - 1; i >= 0; i--) {
  151 |             const form = allForms.nth(i);
  152 |             const nameValue = await form
  153 |                 .locator('input[placeholder="e.g., keycloak"]')
  154 |                 .first()
  155 |                 .inputValue()
  156 |                 .catch(() => "");
  157 |             if (nameValue === "test-issuer") {
  158 |                 await form.getByRole("button", { name: "Remove" }).click();
  159 |                 if (
  160 |                     await confirmButton
  161 |                         .isVisible({ timeout: 2000 })
  162 |                         .catch(() => false)
  163 |                 ) {
  164 |                     await confirmButton.click();
  165 |                 }
  166 |                 break;
  167 |             }
  168 |         }
  169 |     });
  170 | 
  171 |     test("should delete an existing issuer", async ({ customUIFrame }) => {
  172 |         // Add an issuer to delete. Scope every interaction to the newly-added form
  173 |         // (a prior serial-block test may have left other issuer forms present), so
  174 |         // this test removes its OWN issuer rather than whichever form is first.
  175 |         const addIssuerButton = customUIFrame.getByRole("button", {
  176 |             name: "Add Issuer",
  177 |         });
  178 |         const issuerForms = customUIFrame.locator(".issuer-form");
  179 |         const existingCount = await issuerForms.count();
  180 | 
  181 |         await expect(addIssuerButton).toBeVisible({ timeout: 5000 });
  182 |         await addIssuerButton.click();
  183 | 
  184 |         const form = issuerForms.nth(existingCount);
  185 |         const issuerNameInput = form.locator(
  186 |             'input[placeholder="e.g., keycloak"]',
  187 |         );
  188 |         await expect(issuerNameInput).toBeVisible({ timeout: 5000 });
  189 |         await issuerNameInput.fill("delete-me-issuer");
  190 | 
  191 |         const jwksUrlInput = form.locator('input[name="jwks-url"]');
  192 |         await expect(jwksUrlInput).toBeVisible({ timeout: 5000 });
  193 |         await jwksUrlInput.fill("https://example.com/.well-known/jwks.json");
  194 | 
  195 |         const saveButton = form.getByRole("button", { name: "Save Issuer" });
  196 |         await expect(saveButton).toBeVisible({ timeout: 5000 });
  197 |         await saveButton.click();
  198 | 
  199 |         // Verify issuer was saved (name persists in its input field)
  200 |         await expect(issuerNameInput).toHaveValue("delete-me-issuer", {
  201 |             timeout: 5000,
  202 |         });
  203 | 
  204 |         // Remove this issuer via its own form's Remove button.
  205 |         const removeButton = form.getByRole("button", { name: "Remove" });
  206 |         await expect(removeButton).toBeVisible({ timeout: 5000 });
  207 |         await removeButton.click();
  208 | 
  209 |         // The remove button always opens a confirmation dialog; wait for it rather
  210 |         // than probing with a short timeout (slower CI can take >2s to render it).
  211 |         const confirmButton = customUIFrame
  212 |             .locator(
  213 |                 '.confirmation-dialog .confirm-button, button:has-text("Confirm"), button:has-text("Yes")',
  214 |             )
  215 |             .first();
  216 |         await expect(confirmButton).toBeVisible({ timeout: 10000 });
  217 |         await confirmButton.click();
  218 | 
  219 |         // Verify the issuer "delete-me-issuer" is removed. Removal is async
  220 |         // (confirm dialog → API update → re-render); a one-shot read of the input
  221 |         // values raced that re-render and saw the stale value, so poll until no
  222 |         // input field carries the removed issuer name.
  223 |         await expect
  224 |             .poll(
  225 |                 async () => {
  226 |                     const inputs = customUIFrame.locator(
  227 |                         'input[placeholder="e.g., keycloak"]',
  228 |                     );
  229 |                     const n = await inputs.count();
  230 |                     for (let i = 0; i < n; i++) {
  231 |                         if (
  232 |                             (await inputs.nth(i).inputValue()) ===
  233 |                             "delete-me-issuer"
  234 |                         ) {
  235 |                             return true;
  236 |                         }
  237 |                     }
  238 |                     return false;
  239 |                 },
  240 |                 { timeout: 10000 },
  241 |             )
> 242 |             .toBe(false);
      |              ^ Error: Timeout 10000ms exceeded while waiting on the predicate
  243 |     });
  244 | 
  245 |     test("should edit an existing issuer configuration", async ({
  246 |         customUIFrame,
  247 |     }) => {
  248 |         // Add an issuer first
  249 |         const addIssuerButton = customUIFrame.getByRole("button", {
  250 |             name: "Add Issuer",
  251 |         });
  252 |         const issuerForms = customUIFrame.locator(".issuer-form");
  253 |         const existingCount = await issuerForms.count();
  254 | 
  255 |         await addIssuerButton.click();
  256 | 
  257 |         // Target the newly added form
  258 |         const newForm = issuerForms.nth(existingCount);
  259 | 
  260 |         const issuerNameInput = newForm.locator(
  261 |             'input[placeholder="e.g., keycloak"]',
  262 |         );
  263 |         await issuerNameInput.fill("edit-test-issuer");
  264 | 
  265 |         const issuerUriInput = newForm.locator('input[name="issuer"]');
  266 |         await issuerUriInput.fill("https://original-issuer.example.com");
  267 | 
  268 |         const jwksUrlInput = newForm.locator('input[name="jwks-url"]');
  269 |         await jwksUrlInput.fill(
  270 |             "https://original.example.com/.well-known/jwks.json",
  271 |         );
  272 | 
  273 |         const audienceInput = newForm.locator('input[name="audience"]');
  274 |         await audienceInput.fill("original-audience");
  275 | 
  276 |         // Save the initial issuer
  277 |         const saveButton = newForm.getByRole("button", {
  278 |             name: "Save Issuer",
  279 |         });
  280 |         await saveButton.click();
  281 | 
  282 |         const successMessage = newForm.locator(".success-message").first();
  283 |         await expect(successMessage).toBeVisible({ timeout: 10000 });
  284 |         await expect(successMessage).toContainText("saved successfully");
  285 |         // Persistence must actually occur: the ?id=<uuid> component ID drives a real save,
  286 |         // so the persisted message is expected — NOT the "(standalone mode)" fallback, which
  287 |         // would mean the component ID never reached the editor and the save was dropped.
  288 |         await expect(successMessage).not.toContainText("standalone");
  289 | 
  290 |         // Edit the issuer: change audience and JWKS URL
  291 |         await audienceInput.fill("updated-audience");
  292 |         await jwksUrlInput.fill(
  293 |             "https://updated.example.com/.well-known/jwks.json",
  294 |         );
  295 | 
  296 |         // Save again
  297 |         await saveButton.click();
  298 | 
  299 |         // Verify save success
  300 |         await expect(successMessage).toBeVisible({ timeout: 10000 });
  301 |         await expect(successMessage).toContainText("saved successfully");
  302 |         // Persistence must actually occur: the ?id=<uuid> component ID drives a real save,
  303 |         // so the persisted message is expected — NOT the "(standalone mode)" fallback, which
  304 |         // would mean the component ID never reached the editor and the save was dropped.
  305 |         await expect(successMessage).not.toContainText("standalone");
  306 | 
  307 |         // Verify updated values are preserved in the form
  308 |         await expect(audienceInput).toHaveValue("updated-audience");
  309 |         await expect(jwksUrlInput).toHaveValue(
  310 |             "https://updated.example.com/.well-known/jwks.json",
  311 |         );
  312 | 
  313 |         // Clean up: remove the test issuer
  314 |         await newForm.getByRole("button", { name: "Remove" }).click();
  315 | 
  316 |         const confirmButton = customUIFrame
  317 |             .locator(
  318 |                 '.confirmation-dialog .confirm-button, button:has-text("Confirm"), button:has-text("Yes")',
  319 |             )
  320 |             .first();
  321 |         if (await confirmButton.isVisible({ timeout: 2000 })) {
  322 |             await confirmButton.click();
  323 |         }
  324 |     });
  325 | 
  326 |     test("should manage multiple issuers simultaneously", async ({
  327 |         customUIFrame,
  328 |     }) => {
  329 |         const addIssuerButton = customUIFrame.getByRole("button", {
  330 |             name: "Add Issuer",
  331 |         });
  332 |         const issuerForms = customUIFrame.locator(".issuer-form");
  333 | 
  334 |         // Count existing forms before adding
  335 |         const existingCount = await issuerForms.count();
  336 | 
  337 |         // Add first issuer — new form appears at the end
  338 |         await addIssuerButton.click();
  339 |         const firstForm = issuerForms.nth(existingCount);
  340 | 
  341 |         await firstForm
  342 |             .locator('input[placeholder="e.g., keycloak"]')
```