# Instructions

- Following Playwright test failed.
- Explain why, be concise, respect Playwright best practices.
- Provide a snippet of code with the fix, if possible.

# Test info

- Name: 01-verify-configuration-tab.spec.js >> Configuration Tab >> should manage multiple issuers simultaneously
- Location: tests/01-verify-configuration-tab.spec.js:326:5

# Error details

```
TimeoutError: locator.inputValue: Timeout 10000ms exceeded.
Call log:
  - waiting for locator('input[placeholder="e.g., keycloak"]').nth(1)

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
              - generic [ref=f1e17]:
                - generic [ref=f1e18]:
                  - generic [ref=f1e19]:
                    - text: "Issuer Name:"
                    - button "Show field help" [ref=f1e20] [cursor=pointer]:
                      - generic [ref=f1e22]: Show field help
                  - textbox "Issuer Name" [ref=f1e23]:
                    - /placeholder: e.g., keycloak
                    - text: issuer-two
                  - button " Remove" [ref=f1e24] [cursor=pointer]:
                    - generic [ref=f1e25]: 
                    - text: Remove
                - generic [ref=f1e26]:
                  - generic [ref=f1e27]:
                    - generic [ref=f1e28]:
                      - text: "JWKS Source Type:"
                      - button "Show field help" [ref=f1e29] [cursor=pointer]:
                        - generic [ref=f1e31]: Show field help
                    - combobox "JWKS Source Type" [ref=f1e32]:
                      - option "URL (Remote JWKS endpoint)" [selected]
                      - option "File (Local JWKS file)"
                      - option "Memory (Inline JWKS content)"
                  - generic [ref=f1e33]:
                    - generic [ref=f1e34]:
                      - text: "Issuer URI:"
                      - button "Show field help" [ref=f1e35] [cursor=pointer]:
                        - generic [ref=f1e37]: Show field help
                    - textbox "Issuer URI" [ref=f1e38]:
                      - /placeholder: The URI of the token issuer (must match the iss claim)
                      - text: https://issuer-two.example.com
                  - generic [ref=f1e39]:
                    - generic [ref=f1e40]:
                      - text: "JWKS URL:"
                      - button "Show field help" [ref=f1e41] [cursor=pointer]:
                        - generic [ref=f1e43]: Show field help
                    - textbox "JWKS URL" [ref=f1e44]:
                      - /placeholder: The URL of the JWKS endpoint
                      - text: https://issuer-two.example.com/.well-known/jwks.json
                  - generic [ref=f1e45]:
                    - button " Test Connection" [ref=f1e46] [cursor=pointer]:
                      - generic [ref=f1e47]: 
                      - text: Test Connection
                    - status [ref=f1e48]:
                      - emphasis [ref=f1e49]: Click the button to validate JWKS
                  - generic [ref=f1e50]:
                    - generic [ref=f1e51]:
                      - text: "Audience:"
                      - button "Show field help" [ref=f1e52] [cursor=pointer]:
                        - generic [ref=f1e54]: Show field help
                    - textbox "Audience" [ref=f1e55]:
                      - /placeholder: The expected audience claim value
                      - text: sample-audience
                  - generic [ref=f1e56]:
                    - generic [ref=f1e57]:
                      - text: "Client ID:"
                      - button "Show field help" [ref=f1e58] [cursor=pointer]:
                        - generic [ref=f1e60]: Show field help
                    - textbox "Client ID" [ref=f1e61]:
                      - /placeholder: The client ID for token validation
                      - text: sample-client
                - alert
                - button " Save Issuer" [ref=f1e62] [cursor=pointer]:
                  - generic [ref=f1e63]: 
                  - text: Save Issuer
              - button " Add Issuer" [ref=f1e64] [cursor=pointer]:
                - generic [ref=f1e65]: 
                - text: Add Issuer
          - text:              
```

# Test source

```ts
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
  343 |             .fill("issuer-one");
  344 |         await firstForm
  345 |             .locator('input[name="issuer"]')
  346 |             .fill("https://issuer-one.example.com");
  347 |         await firstForm
  348 |             .locator('input[name="jwks-url"]')
  349 |             .fill("https://issuer-one.example.com/.well-known/jwks.json");
  350 | 
  351 |         await firstForm.getByRole("button", { name: "Save Issuer" }).click();
  352 | 
  353 |         // Verify first issuer saved
  354 |         const firstSuccess = firstForm.locator(".success-message");
  355 |         await expect(firstSuccess).toBeVisible({ timeout: 10000 });
  356 | 
  357 |         // Add second issuer — new form appears at the end
  358 |         await addIssuerButton.click();
  359 |         const secondForm = issuerForms.nth(existingCount + 1);
  360 | 
  361 |         await secondForm
  362 |             .locator('input[placeholder="e.g., keycloak"]')
  363 |             .fill("issuer-two");
  364 |         await secondForm
  365 |             .locator('input[name="issuer"]')
  366 |             .fill("https://issuer-two.example.com");
  367 |         await secondForm
  368 |             .locator('input[name="jwks-url"]')
  369 |             .fill("https://issuer-two.example.com/.well-known/jwks.json");
  370 | 
  371 |         await secondForm.getByRole("button", { name: "Save Issuer" }).click();
  372 | 
  373 |         // Verify second issuer saved
  374 |         const secondSuccess = secondForm.locator(".success-message");
  375 |         await expect(secondSuccess).toBeVisible({ timeout: 10000 });
  376 | 
  377 |         // Verify both issuer names are visible
  378 |         const allNameInputs = customUIFrame.locator(
  379 |             'input[placeholder="e.g., keycloak"]',
  380 |         );
  381 |         const names = [];
  382 |         const nameCount = await allNameInputs.count();
  383 |         for (let i = 0; i < nameCount; i++) {
  384 |             names.push(await allNameInputs.nth(i).inputValue());
  385 |         }
  386 |         expect(names).toContain("issuer-one");
  387 |         expect(names).toContain("issuer-two");
  388 | 
  389 |         // Remove first added issuer (issuer-one) via its own Remove button
  390 |         await firstForm.getByRole("button", { name: "Remove" }).click();
  391 | 
  392 |         // The remove button always opens a confirmation dialog; wait for it rather
  393 |         // than probing with a short timeout (slower CI can take >2s to render it,
  394 |         // which previously skipped the confirm and left the issuer in place).
  395 |         const confirmButton = customUIFrame
  396 |             .locator(
  397 |                 '.confirmation-dialog .confirm-button, button:has-text("Confirm"), button:has-text("Yes")',
  398 |             )
  399 |             .first();
  400 |         await expect(confirmButton).toBeVisible({ timeout: 10000 });
  401 |         await confirmButton.click();
  402 | 
  403 |         // Verify only issuer-two remains among the added issuers. Removal is async
  404 |         // (confirm → API update → re-render), so poll rather than reading input
  405 |         // values once (which raced the re-render and still saw issuer-one).
  406 |         const readIssuerNames = async () => {
  407 |             const inputs = customUIFrame.locator(
  408 |                 'input[placeholder="e.g., keycloak"]',
  409 |             );
  410 |             const n = await inputs.count();
  411 |             const out = [];
  412 |             for (let i = 0; i < n; i++) {
> 413 |                 out.push(await inputs.nth(i).inputValue());
      |                                              ^ TimeoutError: locator.inputValue: Timeout 10000ms exceeded.
  414 |             }
  415 |             return out;
  416 |         };
  417 |         await expect
  418 |             .poll(async () => (await readIssuerNames()).includes("issuer-one"), {
  419 |                 timeout: 15000,
  420 |             })
  421 |             .toBe(false);
  422 |         expect(await readIssuerNames()).toContain("issuer-two");
  423 | 
  424 |         // Clean up: remove issuer-two — it's now the last form
  425 |         const lastForm = issuerForms.last();
  426 |         await lastForm.getByRole("button", { name: "Remove" }).click();
  427 |         await expect(confirmButton).toBeVisible({ timeout: 10000 });
  428 |         await confirmButton.click();
  429 |     });
  430 | 
  431 |     test("should save issuer with inline JWKS content", async ({
  432 |         customUIFrame,
  433 |     }) => {
  434 |         const addIssuerButton = customUIFrame.getByRole("button", {
  435 |             name: "Add Issuer",
  436 |         });
  437 |         const issuerForms = customUIFrame.locator(".issuer-form");
  438 |         const existingCount = await issuerForms.count();
  439 | 
  440 |         await addIssuerButton.click();
  441 | 
  442 |         // Target the newly added form
  443 |         const newForm = issuerForms.nth(existingCount);
  444 | 
  445 |         // Fill issuer name and URI
  446 |         const issuerNameInput = newForm.locator(
  447 |             'input[placeholder="e.g., keycloak"]',
  448 |         );
  449 |         await issuerNameInput.fill("memory-issuer");
  450 | 
  451 |         const issuerUriInput = newForm.locator('input[name="issuer"]');
  452 |         await issuerUriInput.fill("https://memory-issuer.example.com");
  453 | 
  454 |         // Switch JWKS Source Type to "Memory"
  455 |         const jwksTypeSelect = newForm.locator('select[name="jwks-type"]');
  456 |         await jwksTypeSelect.selectOption("memory");
  457 | 
  458 |         // Fill textarea with valid JWKS JSON
  459 |         const jwksContentArea = newForm.locator(
  460 |             'textarea[name="jwks-content"]',
  461 |         );
  462 |         await expect(jwksContentArea).toBeVisible({ timeout: 5000 });
  463 | 
  464 |         const validJwks = JSON.stringify({
  465 |             keys: [
  466 |                 {
  467 |                     kty: "RSA",
  468 |                     kid: "test-key-1",
  469 |                     use: "sig",
  470 |                     alg: "RS256",
  471 |                     n: "0vx7agoebGcQSuuPiLJXZptN9nndrQmbXEps2aiAFbWhM78LhWx4cbbfAAtVT86zwu1RK7aPFFxuhDR1L6tSoc_BJECPebWKRXjBZCiFV4n3oknjhMstn64tZ_2W-5JsGY4Hc5n9yBXArwl93lqt7_RN5w6Cf0h4QyQ5v-65YGjQR0_FDW2QvzqY368QQMicAtaSqzs8KJZgnYb9c7d0zgdAZHzu6qMQvRL5hajrn1n91CbOpbISD08qNLyrdkt-bFTWhAI4vMQFh6WeZu0fM4lFd2NcRwr3XPksINHaQ-G_xBniIqbw0Ls1jF44-csFCur-kEgU8awapJzKnqDKgw",
  472 |                     e: "AQAB",
  473 |                 },
  474 |             ],
  475 |         });
  476 |         await jwksContentArea.fill(validJwks);
  477 | 
  478 |         // Save the issuer
  479 |         const saveButton = newForm.getByRole("button", {
  480 |             name: "Save Issuer",
  481 |         });
  482 |         await saveButton.click();
  483 | 
  484 |         // Verify save success
  485 |         const successMessage = newForm.locator(".success-message").first();
  486 |         await expect(successMessage).toBeVisible({ timeout: 10000 });
  487 |         await expect(successMessage).toContainText("saved successfully");
  488 |         // Persistence must actually occur: the ?id=<uuid> component ID drives a real save,
  489 |         // so the persisted message is expected — NOT the "(standalone mode)" fallback, which
  490 |         // would mean the component ID never reached the editor and the save was dropped.
  491 |         await expect(successMessage).not.toContainText("standalone");
  492 | 
  493 |         // Verify JWKS type still shows "Memory"
  494 |         await expect(jwksTypeSelect).toHaveValue("memory");
  495 | 
  496 |         // Verify issuer name is preserved
  497 |         await expect(issuerNameInput).toHaveValue("memory-issuer");
  498 | 
  499 |         // Clean up: remove the test issuer
  500 |         await newForm.getByRole("button", { name: "Remove" }).click();
  501 | 
  502 |         const confirmButton = customUIFrame
  503 |             .locator(
  504 |                 '.confirmation-dialog .confirm-button, button:has-text("Confirm"), button:has-text("Yes")',
  505 |             )
  506 |             .first();
  507 |         if (await confirmButton.isVisible({ timeout: 2000 })) {
  508 |             await confirmButton.click();
  509 |         }
  510 |     });
  511 | 
  512 |     test("should handle duplicate issuer names", async ({
  513 |         customUIFrame,
```