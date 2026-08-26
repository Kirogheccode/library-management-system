# Bug Report

    Project: Modern Library Management System
    Course: CS300 – CSC13002 – Introduction to Software Engineering
    Group ID: 03
    Group Name: AmeThyst
    Assignment: PA5-2026
    Version: 1.5

Performed by: All Members | Reviewed by: All Members | Edited by: Vũ Duy Nhất

---
## Revision History
| Date | Version | Description | Author |
| :--- | :--- | :--- | :--- |
| 14/08/2026 | 1.0 | Template for Bug Report | Nguyễn Lê Hoàng Khải |
| 15/08/2026 | 1.1 | Bug Report for Register and Resend Verification | Phan Lê Anh Minh |
| 16/08/2026 | 1.2 | Bug Report for Reserve Book and Verify PIN | Nguyễn Nhựt Huy |
| 21/08/2026 | 1.3 | Update status for bugs in Register and Resend Verification | Phan Lê Anh Minh |
| 21/08/2026 | 1.4 | Combine all and Edit | Vũ Duy Nhất |
| 23/08/2026 | 1.5 | Update Bug Report for Register and Resend Verification | Phan Lê Anh Minh |


## Table of Contents

- [Bug Report](#bug-report)
  - [Revision History](#revision-history)
  - [Table of Contents](#table-of-contents)
  - [I. Test Summary](#i-test-summary)
  - [II. Bug Reports](#ii-bug-reports)
    - [2.1 Register](#21-register)
    - [2.2 Resend Verification](#22-resend-verification)
    - [2.3 Reserve Book](#23-reserve-book)
    - [2.4 Verify PIN](#24-verify-pin)

## I. Test Summary
Execution covered the full set of **131 test cases** defined in the **Test Plan and Test Cases** document, spanning the Middleware, API/Integration, Controller, and Service layers across all eight implemented features (Register, Google OAuth, Resend Verification, Verify Email, Reserve Book, Verify PIN, Create Study Group, AI Recommendation). Testing combined the automated Vitest suite (`npm test` / feature-specific scripts, from `src/server`) with mocked PostgreSQL, mail, and session dependencies, cross-checked by manual functional testing through the web client and API. Execution ran between **2026-08-13** and **2026-08-21**.

**Overall statistics:**

| Metric | Count |
| :--- | :--- |
| Number of features tested | 8 |
| Total test cases executed | 131 |
| Passed (initial run) | 124 |
| Failed (initial run) | 10 |
| Pass rate (initial run) | 94.7% |
| Defects logged | 10 (BUG-01→10) |
| Defects fixed & re-verified | 10 (BUG-01→10) |
| Defects still open | 0 |
| Effective passing (after 2026-08-23 regression) | 131 / 131 |

**Results by feature:**

| Feature | Test Cases | Passed | Failed | Linked Bug(s) | Execution Date(s) | Fixed All
| :--- | :---: | :---: | :---: | :--- | :--- | :---: |
| Register | 10 | 8 | 2 | BUG-01, BUG-02 | 2026-08-14 - 2026-08-21 | Yes |
| Google OAuth | 10 | 10 | 0 | — | 2026-08-14 - 2026-08-21 | — |
| Resend Verification | 10 | 7 | 3 | BUG-03, BUG-04, BUG-05 | 2026-08-14 - 2026-08-21 | Yes |
| Verify Email | 10 | 10 | 0 | — | 2026-08-14 - 2026-08-21 | — |
| Reserve Book | 10 | 9 | 1 | BUG-01 | 2026-08-13 – 2026-08-16 | Yes |
| Verify PIN | 40 | 36 | 4 | BUG-02, BUG-03, BUG-04, BUG-05 | 2026-08-13 – 2026-08-16 | Yes |
| Create Study Group | 30 | 30 | 0 | — | 2026-08-16 |
| AI Recommendation | 11 | 11 | 0 | — | 2026-08-21 |
| **Total** | **118** | **111** | **7** | **10 defects** | **2026-08-13 – 2026-08-21** | **Yes** |

## II. Bug Reports

### 2.1 Register

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Bug Report: BUG-01
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Bug ID</td>
      <td style="vertical-align: top;"><strong>BUG-01</strong></td>
    </tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Linked Test Case ID</td><td style="vertical-align: top;">TC-SRV-REG-003</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Initial registration commits pending data before verification email delivery succeeds.</td></tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Steps to Reproduce</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Configure successful database operations.</li>
          <li>Call registerUser with valid data.</li>
          <li>Make the verification mailer reject.</li>
          <li>Inspect the final pending-registration state.</li>
        </ol>
      </td>
    </tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Result</td><td style="vertical-align: top;">Failed initial delivery does not leave newly committed pending data.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Actual Result</td><td style="vertical-align: top;">The pending record remains committed although the email was not delivered.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Severity</td><td style="vertical-align: top;">High</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Status</td><td style="vertical-align: top;">Fixed (re-verified 2026-08-21)</td></tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Bug Report: BUG-02</th></tr></thead>
<tbody>
<tr><td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Bug ID</td><td><strong>BUG-02</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Linked Test Case ID</td><td>TC-INT-REG-005</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td>After an initial registration email fails, an immediate retry is treated as an active pending registration and does not create or deliver a fresh token.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Steps to Reproduce</td><td><ol><li>POST a valid unused registration and make its mail delivery reject.</li><li>Confirm the first request returns HTTP 502.</li><li>Immediately POST the same registration again.</li><li>Inspect the second response, token state, and mailer call count.</li></ol></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Result</td><td>The retry creates a fresh pending token and performs a second delivery attempt.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Actual Result</td><td>The retry returns the generic HTTP 201 response, but no fresh token is issued and the mailer runs only once across both requests.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Severity</td><td>High</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Status</td><td>Fixed (re-verified 2026-08-23)</td></tr>
</tbody></table>

### 2.2 Resend Verification

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Bug Report: BUG-03
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Bug ID</td>
      <td style="vertical-align: top;"><strong>BUG-03</strong></td>
    </tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Linked Test Case ID</td><td style="vertical-align: top;">TC-SRV-RV-003</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Resend verification replaces the previous token before successful email delivery is confirmed.</td></tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Steps to Reproduce</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Create a pending registration with a valid token and TTL.</li>
          <li>Configure the replacement verification mailer to reject.</li>
          <li>Call the resend service.</li>
          <li>After the rejection, inspect the stored token and TTL.</li>
        </ol>
      </td>
    </tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Result</td><td style="vertical-align: top;">The previous token and TTL remain usable when replacement email is not delivered.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Actual Result</td><td style="vertical-align: top;">The replacement token and TTL are committed before delivery fails.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Severity</td><td style="vertical-align: top;">High</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Status</td><td style="vertical-align: top;">Fixed (re-verified 2026-08-21)</td></tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Bug Report: BUG-04</th></tr></thead>
<tbody>
<tr><td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Bug ID</td><td><strong>BUG-04</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Linked Test Case ID</td><td>TC-INT-RV-003</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td>The resend API exposes the undelivered replacement token as persisted state while email delivery is in progress.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Steps to Reproduce</td><td><ol><li>Start a resend request for an active pending registration.</li><li>Hold the mail delivery promise unresolved.</li><li>Inspect persisted token and TTL at the delivery boundary.</li><li>Reject delivery and inspect the HTTP response and final state.</li></ol></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Result</td><td>Persisted state remains on the previous token throughout delivery; a failed delivery returns HTTP 502 without changing it.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Actual Result</td><td>The request eventually returns HTTP 502 and restores the old state, but the persisted token at the delivery boundary is the undelivered replacement.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Severity</td><td>High</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Status</td><td>Fixed (re-verified 2026-08-23)</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Bug Report: BUG-05</th></tr></thead>
<tbody>
<tr><td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Bug ID</td><td><strong>BUG-05</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Linked Test Case ID</td><td>TC-INT-RV-004</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td>The previously valid verification token becomes unusable while a resend delivery is pending, even when that replacement delivery later fails.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Steps to Reproduce</td><td><ol><li>Create a pending registration with an active token.</li><li>Start resend and hold replacement delivery unresolved.</li><li>Submit the previous token to <code>/auth/verify-email</code>.</li><li>Reject resend delivery and inspect both responses and final state.</li></ol></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Result</td><td>The previous token remains verifiable while resend is in progress; verification returns HTTP 200 and failed resend does not invalidate it.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Actual Result</td><td>Verification with the previous token returns HTTP 400 while resend is pending; the resend later returns HTTP 502 and restores the old token.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Severity</td><td>High</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Status</td><td>Fixed (re-verified 2026-08-23)</td></tr>
</tbody></table>

### 2.3 Reserve Book

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Bug Report: BUG-06
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Bug ID</td>
      <td style="vertical-align: top;"><strong>BUG-06</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Linked Test Case ID</td>
      <td style="vertical-align: top;">TC-SRV-RES-010</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">The borrow limit is not enforced during reservation. A user whose `borrow_num` equals `MAX_BORROW_LIMIT` could still reserve another book, so `BORROW_LIMIT_EXCEEDED` was never returned.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Steps to Reproduce</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Set user `u-001`'s `borrow_num` to `MAX_BORROW_LIMIT`.</li>
          <li>Send `POST /api/library/reserve` with a valid book and branch.</li>
          <li>Observe that the reservation succeeds and the inventory is decremented.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Result</td>
      <td style="vertical-align: top;">HTTP 400 `BORROW_LIMIT_EXCEEDED` ("You have reached the maximum borrow limit of {limit} books") and the transaction is rolled back.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Actual Result</td>
      <td style="vertical-align: top;">The reservation was accepted (HTTP 201), `available_quantity` was decremented, and `borrow_num` was incremented beyond the limit.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Severity</td>
      <td style="vertical-align: top;">High</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Status</td>
      <td style="vertical-align: top;">Fixed (re-verified 2026-08-16)</td>
    </tr>
  </tbody>
</table>

### 2.4 Verify PIN

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Bug Report: BUG-07
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Bug ID</td>
      <td style="vertical-align: top;"><strong>BUG-07</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Linked Test Case ID</td>
      <td style="vertical-align: top;">TC-SRV-PIN-US-004</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">A PIN collision during pickup-PIN generation crashed the endpoint with an uncaught database unique-violation (SQLSTATE 23505) instead of retrying with a new random candidate.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Steps to Reproduce</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Force every generated candidate PIN to collide with an existing active PIN.</li>
          <li>Click "View PIN" on a reserved book card.</li>
          <li>Observe an uncaught duplicate-key error / 500 crash.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Result</td>
      <td style="vertical-align: top;">Retry generation up to 3 times; if all attempts collide, return HTTP 500 `PIN_GENERATION_FAILED` ("Failed to generate unique PIN after 3 attempts") without crashing.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Actual Result</td>
      <td style="vertical-align: top;">The first duplicate-key error propagated out of the service (uncaught), crashing the request with a raw database error.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Severity</td>
      <td style="vertical-align: top;">High</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Status</td>
      <td style="vertical-align: top;">Fixed (re-verified 2026-08-16)</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Bug Report: BUG-08
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Bug ID</td>
      <td style="vertical-align: top;"><strong>BUG-08</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Linked Test Case ID</td>
      <td style="vertical-align: top;">TC-SRV-PIN-LIB-005 / TC-CTL-PIN-LIB-004</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">A librarian at one branch could verify a pickup PIN whose reservation belonged to another branch; the branch match was never checked, so `WRONG_BRANCH` was never returned.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Steps to Reproduce</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Generate a pickup PIN for a reservation with `branch_id = 2`.</li>
          <li>Log in as a librarian whose `branch_id = 1`.</li>
          <li>Submit the PIN to `verifyPin`; observe that verification succeeds.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Result</td>
      <td style="vertical-align: top;">HTTP 403 `WRONG_BRANCH` ("You have arrived at the wrong book borrowing branch.") when the reservation branch differs from the librarian's branch.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Actual Result</td>
      <td style="vertical-align: top;">The cross-branch PIN was accepted and borrower/book details were returned.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Severity</td>
      <td style="vertical-align: top;">High</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Status</td>
      <td style="vertical-align: top;">Fixed (re-verified 2026-08-16)</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Bug Report: BUG-09
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Bug ID</td>
      <td style="vertical-align: top;"><strong>BUG-09</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Linked Test Case ID</td>
      <td style="vertical-align: top;">TC-SRV-PIN-LIB-016</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Confirming the return of a lost book did not charge the 2× price penalty; no `book_penalty` row was inserted and `penaltyAmount` stayed 0.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Steps to Reproduce</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Start with a borrow record in `pending_return` whose book price is 50.</li>
          <li>Call `confirmReturn` with `is_lost = true` (lost book).</li>
          <li>Observe `penaltyAmount = 0` and no `book_penalty` row.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Result</td>
      <td style="vertical-align: top;">A `book_penalty` row of 2 × 50 = 100 is inserted; result reports `penaltyAmount = 100`, `issue = "lost"`, `inventoryUpdated = false`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Actual Result</td>
      <td style="vertical-align: top;">No penalty recorded; `penaltyAmount = 0`, `issue` was null and the lost-book path was silently skipped.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Severity</td>
      <td style="vertical-align: top;">Medium</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Status</td>
      <td style="vertical-align: top;">Fixed (re-verified 2026-08-16)</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Bug Report: BUG-10
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Bug ID</td>
      <td style="vertical-align: top;"><strong>BUG-10</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Linked Test Case ID</td>
      <td style="vertical-align: top;">TC-SRV-PIN-LIB-019</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">After a successful return, the `pin` and `expired_at` values were not cleared from the `borrow_book` row, so the return PIN remained reusable.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Steps to Reproduce</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Generate a return PIN for a borrowed book (status `pending_return`).</li>
          <li>Confirm the return via `confirmReturn`.</li>
          <li>Query `borrow_book`; the `pin`/`expired_at` columns still contain the previous values.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Result</td>
      <td style="vertical-align: top;">`pin` and `expired_at` are set to NULL on the confirmed return so the PIN cannot be reused.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Actual Result</td>
      <td style="vertical-align: top;">The PIN remained stored and could be used again against the same record.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Severity</td>
      <td style="vertical-align: top;">Medium</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Status</td>
      <td style="vertical-align: top;">Fixed (re-verified 2026-08-16)</td>
    </tr>
  </tbody>
</table>
