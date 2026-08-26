# Test Case

    Project: Modern Library Management System
    Course: CS300 – CSC13002 – Introduction to Software Engineering
    Group ID: 03
    Group Name: AmeThyst
    Assignment: PA5-2026
    Version: 1.8

Performed by: All Members | Reviewed by: All Members | Edited by: Vũ Duy Nhất

---

## Revision History
| Date | Version | Description | Author |
| :--- | :--- | :--- | :--- |
| 14/08/2026 | 1.0 | Template for Test Case | Nguyễn Lê Hoàng Khải |
| 15/08/2026 | 1.1 | Test Case Description for Create Study Group | Nguyễn Lê Hoàng Khải |
| 15/08/2026 | 1.2 | Test Case Description for Register, Google OAuth, Verify Email, Resend Verification | Phan Lê Anh Minh |
| 16/08/2026 | 1.3 | Test Case Description for Reserve Book and Verify PIN | Nguyễn Nhựt Huy |
| 16/08/2026 | 1.4 | Update more test cases for Create Study Group | Nguyễn Lê Hoàng Khải |
| 21/08/2026 | 1.5 | Test Case Description for AI Recommendation | Trần Lê Hoàng Gia |
| 21/08/2026 | 1.6 | Combine all and Edit | Vũ Duy Nhất |
| 23/08/2026 | 1.7 | Expand Register/Email Verification/Resend Verification/Google OAuth to 10 test cases each | Phan Lê Anh Minh |
| 26/08/2026 | 1.8 | Add Spec Kit / Review / Adjustment traceability fields to all test cases | Vũ Duy Nhất |


## Table of Contents

- [Test Case](#test-case)
  - [Revision History](#revision-history)
  - [Table of Contents](#table-of-contents)
  - [I. Register](#i-register)
  - [II. Google OAuth](#ii-google-oauth)
  - [III. Resend Verification](#iii-resend-verification)
  - [IV. Verify Email](#iv-verify-email)
  - [V. Reserve Book](#v-reserve-book)
  - [VI. Verify PIN](#vi-verify-pin)
  - [VII. Create Study Group](#vii-create-study-group)
  - [VIII. AI Recommendation](#viii-ai-recommendation)

---

## I. Register

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Secure successful registration</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-SRV-REG-001</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Secure successful registration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Registration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid unused email, username, and plaintext password.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Call registerUser ; inspect hashing, pending persistence, transaction-before-mail order, mail arguments, and response.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">Password is hashed, plaintext is not persisted, pending data is committed, verification mail is sent, and the generic confirmation is returned.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Exact pending-expiration boundary</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-SRV-REG-002</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Exact pending-expiration boundary.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Registration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Pending row whose expired_at equals the frozen current time.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Freeze time; call registerUser ; inspect deletion and continuation.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">The row is expired at equality, is deleted, and does not block a fresh registration.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: equality was accepted as active. Revised: equality is expired.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Aligns with the current now &gt;= expired_at lifecycle and avoids accepting a zero-lifetime record.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Initial mail-delivery consistency</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-SRV-REG-003</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Initial mail-delivery consistency.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Registration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid registration; mailer rejects after pending persistence.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Model persisted pending state; invoke the service; reject delivery; inspect final state.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">The typed delivery error is returned and no newly committed unusable pending registration remains.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Controller success mapping</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CTL-REG-001</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Controller success mapping.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Registration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid request body and successful service result.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke register ; inspect service arguments, status, and body.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">The controller delegates all fields and returns HTTP 201 with the generic confirmation.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Controller anti-email-enumeration mapping</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CTL-REG-002</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Controller anti-email-enumeration mapping.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Registration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Existing email hidden by the service's generic result.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke the controller and inspect status/body.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 201 and the same generic message are returned; account existence is not disclosed.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: duplicate email produced a distinct conflict response. Revised: duplicate and unused emails share the generic 201 response.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Enforces the approved anti-email-enumeration requirement.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Registration API success</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-REG-001</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Registration API success.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Registration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid unused registration body.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">POST /auth/register ; inspect status/body, transaction, and mail call.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 201 returns the generic confirmation after pending persistence and delivery request.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Existing-user privacy at the API</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-REG-002</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Existing-user privacy at the API.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Registration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid body using an existing user's email.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">POST registration; inspect response and mailer calls.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 201 returns the generic confirmation and no email is sent.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: duplicate email produced HTTP 409. Revised: it produces the same generic HTTP 201 response.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Prevents email-address enumeration through the HTTP contract.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Active pending-registration handling</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-REG-003</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Active pending-registration handling.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Registration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid request for an email with an unexpired pending row.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">POST registration; inspect response, database connection, and mailer.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 201 returns the generic message without replacing the active row or sending another message.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; this is a newly added boundary scenario.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Registration request validation</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-REG-004</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Registration request validation.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Registration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Malformed email, weak password, and empty username.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">POST the invalid body; inspect validation response and side effects.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 400 returns VALIDATION_ERROR ; no persistence, hashing, or mail occurs.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; this is a newly added validation scenario.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Retry after failed initial delivery</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-REG-005</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Retry after failed initial delivery.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Registration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">First mail attempt rejects; immediate retry uses the same valid body.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Model committed pending state; POST twice; inspect both responses, delivery count, and token replacement.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">First request returns 502; retry creates a fresh pending token and performs a second delivery attempt instead of being blocked by stale state.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A</td></tr>
</tbody></table>



## II. Google OAuth

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: First-time provisioning with avatar</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CFG-GA-001</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">First-time provisioning with avatar.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Google OAuth.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Verified Google email, display name, and photo.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Return no user; invoke verify callback; inspect lookup, insert mapping, and done .</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">A GOOGLE_AUTH user with default user role and supplied avatar is returned.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; the compound case was narrowed.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Returning Google user</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CFG-GA-002</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Returning Google user.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Google OAuth.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Existing user with password_hash = GOOGLE_AUTH .</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke callback; inspect query count, absence of insert, and done .</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">Existing user is returned without duplicate insertion.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; the compound case was narrowed.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: First-time provisioning without avatar</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CFG-GA-003</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">First-time provisioning without avatar.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Google OAuth.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Verified email and display name with no photos.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Return no user; invoke callback; inspect insertion and done .</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">A GOOGLE_AUTH user is inserted with avatar = null .</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No — split from the first Feature 022 compound provisioning case.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; only executable independence changed.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Password-account collision</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CFG-GA-004</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Password-account collision.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Google OAuth.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Existing user with bcrypt password hash.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke callback; inspect query count and refusal result.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">Authentication is refused with account_exists_with_password and no insert occurs.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No — split from the second Feature 022 compound Google-user case.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; only executable independence changed.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Verified-email requirement</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CFG-GA-005</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Verified-email requirement.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Google OAuth.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Profile containing only an explicitly unverified email.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke callback; inspect database calls and refusal result.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">Authentication is refused with verified_email_required before any database query.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; this is a newly added security scenario.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: OAuth controller session redirect</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CTL-GA-001</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">OAuth controller session redirect.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Google OAuth.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Authenticated Google user.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke callback handler; inspect session, cookies, redirect, and next .</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">Session cookies are set and redirect targets CLIENT_URL/auth/callback without a query token.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: controller signed a JWT and placed token/user in the URL. Revised: it creates a cookie session and uses a clean callback URL.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Prevents sensitive query-string exposure and aligns with session authentication.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: OAuth redirect sensitive-data protection</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CTL-GA-002</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">OAuth redirect sensitive-data protection.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Google OAuth.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">User object containing internal authentication fields.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke callback; inspect complete redirect URL.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">URL contains neither password_hash nor GOOGLE_AUTH .</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: OAuth initiation redirect</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-GA-001</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">OAuth initiation redirect.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Google OAuth.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">GET /auth/google .</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Send request; inspect status and Location.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 302 redirects to Google's authorization endpoint.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Successful OAuth callback</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-GA-002</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Successful OAuth callback.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Google OAuth.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Successful mocked Passport callback.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">GET callback; inspect session call and Location.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 302 redirects to the clean client callback and a session is created; no token is in the URL.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: callback redirected with JWT and serialized user query parameters. Revised: callback creates a cookie session and redirects without credentials.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Aligns with the secure session-based callback contract.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Refused OAuth callback redirect</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-GA-003</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Refused OAuth callback redirect.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Google OAuth.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Passport refusal for a password-account collision.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">GET callback; inspect redirect and session calls.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 302 redirects to client login and no session is created.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; this is a newly added failure-path scenario.</td></tr>
</tbody></table>

## III. Resend Verification

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Successful resend</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-SRV-RV-001</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Successful resend.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Resend Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Existing pending registration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Call service; inspect reused credentials, new token/TTL, ordering, mail, and response.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">A new token and later TTL commit, existing hash/name are reused, mail is sent, and the generic response returns.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: No-pending anti-enumeration</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-SRV-RV-002</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">No-pending anti-enumeration.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Resend Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Email with no pending row.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Call service; inspect response and side effects.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">The same generic response returns without replacement or mail.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: absence produced a distinct error. Revised: absence returns the generic confirmation.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Enforces anti-email-enumeration for pending registrations.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Service-level pre-delivery consistency</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-SRV-RV-003</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Service-level pre-delivery consistency.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Resend Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Active old token/TTL; replacement mail rejects.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Model real replacement/restoration semantics; capture stored state when mail delivery starts; inspect final state after rejection.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">The old token/TTL remain committed until delivery succeeds and remain unchanged after failure.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: restoring the old token after delivery failure was sufficient. Revised: the old token/TTL must remain committed until replacement delivery succeeds.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Post-failure compensation leaves an observable invalid-token window; the transaction-consistency requirement promises continued usability, not only eventual restoration.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Controller successful response</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CTL-RV-001</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Controller successful response.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Resend Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid email and successful generic service result.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke controller; inspect delegation, status, and body.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 200 returns the generic confirmation.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; the compound case was narrowed to one scenario.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Unexpected-infrastructure privacy</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CTL-RV-002</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Unexpected-infrastructure privacy.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Resend Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid request; untyped service exception.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke controller; make service throw; inspect response.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 200 returns the generic response without infrastructure details.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: unexpected failure returned HTTP 500 with error details. Revised: untyped failures return the generic HTTP 200 response.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Preserves the approved privacy contract; typed delivery failure remains separately mapped to HTTP 502.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Missing-email validation</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CTL-RV-003</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Missing-email validation.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Resend Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Request body without email.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke controller; inspect service calls and response.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 400 returns Email is required and service is not called.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No — split from a Feature 022 compound case.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; only executable independence changed.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Resend API success</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-RV-001</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Resend API success.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Resend Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Pending registration email.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">POST resend; inspect inserted values, transaction, mail call, status, and body.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">Replacement data commits, mail is requested, and HTTP 200 returns the generic response.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: No-pending privacy at the API</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-RV-002</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">No-pending privacy at the API.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Resend Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid email without pending row.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">POST resend; inspect response and mail calls.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 200 returns the generic confirmation and no email is sent.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: no row returned HTTP 400. Revised: it returns generic HTTP 200.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Prevents enumeration of pending registrations.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: HTTP-level pre-delivery state consistency</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-RV-003</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">HTTP-level pre-delivery state consistency.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Resend Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Active old token/TTL and a mailer that rejects.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">POST resend with stateful database mocks; capture persisted state at the mail boundary and after the 502 response.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">The old token/TTL remain committed throughout; the request returns 502 and final state is unchanged.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Old token remains verifiable during a failed resend</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-RV-004</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Old token remains verifiable during a failed resend.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Resend Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Active old token; replacement delivery held pending and then rejected.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Start resend; while mail is unresolved, POST old token to verification; reject mail; inspect both responses and restored state.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">The old token verifies successfully while resend is pending; resend returns 502 and restores/retains the old state.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A</td></tr>
</tbody></table>



## IV. Verify Email

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Successful pending-user promotion</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-SRV-VE-001</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Successful pending-user promotion.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Email Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid unexpired token for an unregistered pending email.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Call verifyEmail ; inspect insertion, token deletion, and payload.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">Promotion and deletion occur atomically; the safe { user, userRow } result contains no password hash or JWT field.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: service returned a signed JWT with the user. Revised: service returns user data for controller-managed cookie-session creation and no JWT response field.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Aligns with the approved session-based authentication design and protects bearer credentials.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Exact verification-token expiration boundary</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-SRV-VE-002</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Exact verification-token expiration boundary.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Email Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Token whose expired_at equals current time.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Freeze time; verify; inspect cleanup and promotion calls.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">Verification is rejected, the expired row is deleted, and no user is promoted.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: equality remained valid. Revised: equality is expired.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Aligns boundary semantics with now &gt;= expired_at and the approved TTL interpretation.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Duplicate email during verification</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-SRV-VE-003</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Duplicate email during verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Email Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid pending token whose email now exists in users.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Call service; return an existing user; inspect cleanup and insertion calls.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">The pending token is deleted, Email already exists. is thrown, and no duplicate user is inserted.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Controller session mapping</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CTL-VE-001</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Controller session mapping.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Email Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid token and verified user result.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke handler; inspect session creation, cookies, status, and body.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 200 returns only { user: session.user } after session cookies are set.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: response exposed a JWT. Revised: protected cookies carry the session and the body contains only the user.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Session-based authentication replaced browser-readable bearer-token responses.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Missing-token controller response</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CTL-VE-002</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Missing-token controller response.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Email Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Request body without token.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke handler; inspect service calls, status, and body.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 400 returns Verification token is required and the service is not called.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; the compound case was narrowed to one scenario.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Expired-token controller response</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-CTL-VE-003</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Expired-token controller response.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Email Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Service expiration error.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Invoke handler with a token; make service reject as expired; inspect response.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 410 returns the expiration message.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No — split from a Feature 022 compound case.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; only executable independence changed.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Verification API success</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-VE-001</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Verification API success.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Email Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Valid unexpired token and pending row.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">POST verification; inspect transaction, session creation, status, and body.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 200 returns the session user without a token field and promotion commits.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">Original: API returned { token, user } . Revised: API creates a protected-cookie session and returns { user } only.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">Aligns the expected result with the approved session architecture and prevents token exposure.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Missing-token API request</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-VE-002</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Missing-token API request.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Email Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Empty JSON body.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">POST verification; inspect status/body and session calls.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 400 returns the required-token error and no session is created.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Non-existent token rejection</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-VE-003</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Non-existent token rejection.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Email Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Unknown token.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">POST token with no matching row; inspect status/body and session calls.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 400 returns Invalid or expired verification link. ; no session is created.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; this is a newly added negative scenario.</td></tr>
</tbody></table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
<thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Successful token cannot be reused</th></tr></thead>
<tbody>
<tr><td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-INT-VE-004</strong></td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Successful token cannot be reused.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Email Verification.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Same valid token submitted twice.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;">Model deletion on first promotion; POST twice; inspect statuses and session count.</td></tr>
<tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">First request succeeds; second returns HTTP 400; exactly one session is created.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td><td style="vertical-align: top;">No.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td><td style="vertical-align: top;">Yes.</td></tr>
<tr><td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td><td style="vertical-align: top;">Phan Lê Anh Minh.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td><td style="vertical-align: top;">None.</td></tr>
<tr><td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td><td style="vertical-align: top;">N/A; this is a newly added replay-prevention scenario.</td></tr>
</tbody></table>



## V. Reserve Book
<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Successfully reserve an available book
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-RES-001 / TC-SRV-RES-001</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that a logged-in member can successfully reserve an available book at a selected branch and receives the full reservation payload. (Maps to TC-CTL-RES-001 / TC-SRV-RES-001)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Reserve a Book</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Authenticated user `u-001`; `POST /api/library/reserve` with body `{ "bookId": "b-001", "branchId": 1 }`; branch 1 has `available_quantity &ge; 1` for the book.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Log in as a member and open the book detail page for a book with available copies.</li>
          <li>Select branch 1 (Main Branch) and click "Reserve".</li>
          <li>Confirm the reservation and inspect the API response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 201 with `{ success: true, data: { reservationId, bookId: "b-001", branchId: 1, branchName: "Main Branch", branchAddress: "123 Main St", shelf, reserveDate, status: "reserved" } }`; UI shows the "Reserved" state.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Inventory and borrow_book row updated on reservation
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-RES-002</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that a successful reservation decrements `library.available_quantity` by exactly 1 at the selected branch and inserts a `borrow_book` row with status `reserved`. (Maps to TC-SRV-RES-002)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Reserve a Book</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">User `u-001`, book `b-001`, branch 1 with `available_quantity = 2`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Reserve the book via the API/UI as in TC-CTL-RES-001 / TC-SRV-RES-001.</li>
          <li>Query `public.library` for the (book, branch) pair and `public.borrow_book` for the user's newest row.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">`available_quantity` decreased from 2 to 1; a `borrow_book` row exists for (`u-001`, `b-001`, branch 1) with status `reserved`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: User borrow count incremented on reservation
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-RES-003</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that the member's `borrow_num` is incremented by 1 after a successful reservation. (Maps to TC-SRV-RES-003)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Reserve a Book</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">User `u-001` with `borrow_num = 0` before the reservation.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Reserve a book as in TC-CTL-RES-001 / TC-SRV-RES-001.</li>
          <li>Query `public.users.borrow_num` for `u-001`.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">`borrow_num` is now 1 (incremented exactly once).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Missing bookId rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-RES-003</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that a reservation request without `bookId` is rejected before reaching the service layer. (Maps to TC-CTL-RES-003)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Reserve a Book</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`POST /api/library/reserve` with body `{ "branchId": 1 }` (no `bookId`).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Send the reservation request without `bookId`.</li>
          <li>Inspect the HTTP status and response body.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 400 with `{ success: false, error: { code: "MISSING_PARAMETERS", message: "bookId and branchId are required" } }`; the reservation service is not invoked.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Missing branchId rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-RES-004</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that a reservation request without `branchId` is rejected before reaching the service layer. (Maps to TC-CTL-RES-004)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Reserve a Book</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`POST /api/library/reserve` with body `{ "bookId": "b-001" }` (no `branchId`).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Send the reservation request without `branchId`.</li>
          <li>Inspect the HTTP status and response body.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 400 with `{ success: false, error: { code: "MISSING_PARAMETERS", message: "bookId and branchId are required" } }`; the reservation service is not invoked.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Non-existent user account rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-RES-008</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that reserving a book when the authenticated user no longer exists returns `USER_NOT_FOUND` and rolls back the transaction. (Maps to TC-SRV-RES-008)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Reserve a Book</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">User `u-001` whose row is absent from `public.users`; valid book/branch.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Attempt a reservation with a user account that has been deleted from the database.</li>
          <li>Inspect the response and the executed SQL (transaction must roll back).</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 404 `{ code: "USER_NOT_FOUND", message: "User account not found. Please re-login." }`; `ROLLBACK` executed, `COMMIT` not executed.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Unpaid penalties block reservation
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-RES-009</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that a user with unpaid penalties cannot reserve a new book and the transaction is rolled back. (Maps to TC-SRV-RES-009)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Reserve a Book</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">User `u-001` with at least one unpaid penalty (`COUNT(*)` of unpaid = 1).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Attempt a reservation with a user who has an outstanding unpaid penalty.</li>
          <li>Inspect the response and confirm no inventory change occurred.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 400 `{ code: "UNPAID_DEBT", message: "You have unpaid debts. Please clear all outstanding penalties before reserving a new book." }`; `ROLLBACK` executed.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Borrow limit exceeded rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-RES-010</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that a reservation is rejected with `BORROW_LIMIT_EXCEEDED` when the user has already reached the maximum borrow limit, and the transaction is rolled back. (Maps to TC-SRV-RES-010)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Reserve a Book</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">User `u-001` whose `borrow_num` equals `MAX_BORROW_LIMIT`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Set the user's borrow count to the maximum allowed limit.</li>
          <li>Attempt a new reservation and inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 400 `{ code: "BORROW_LIMIT_EXCEEDED", message: "You have reached the maximum borrow limit of {limit} books" }`; `ROLLBACK` executed.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Book not stocked at branch rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-RES-011</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that reserving a book that is not stocked at the selected branch returns `BOOK_NOT_FOUND` and rolls back the transaction. (Maps to TC-SRV-RES-011)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Reserve a Book</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Book `b-001` with no inventory row for branch 1 (`available_quantity, shelf` query returns zero rows).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Attempt to reserve a book at a branch where it has no inventory entry.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 404 `{ code: "BOOK_NOT_FOUND", message: "Book not found at the selected branch" }`; `ROLLBACK` executed.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Unavailable book rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-RES-012 / TC-CTL-RES-007</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that reserving a book with zero available copies at the branch returns `BOOK_UNAVAILABLE` and rolls back the transaction. (Maps to TC-SRV-RES-012 / TC-CTL-RES-007)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Reserve a Book</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Book `b-001` with `available_quantity = 0` at branch 1.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Attempt to reserve a book whose available quantity at the branch is 0.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 400 `{ code: "BOOK_UNAVAILABLE", message: "No available copies at the selected branch" }`; `ROLLBACK` executed.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>


## VI. Verify PIN

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Generate a 6-digit pickup PIN
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-US-001</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that generating a pickup PIN for a `reserved` book produces a unique 6-digit PIN, sets the status to `pending`, and returns an expiry 180 seconds in the future. (Maps to TC-SRV-PIN-US-001)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Pickup PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">User `u-001`, reservation `bb-001` in status `reserved`; request `POST /api/dashboard/user/reservations/bb-001/pin`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>In the "Currently Borrowing" tab, click "View PIN" on a reserved book card.</li>
          <li>Verify the PIN modal opens with a 6-digit code and a countdown timer.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">PIN matches `/^\d{6}$/`; `borrow_book.status` = `pending`; `expiresAt` is a `Date` approximately 180,000 ms (3 minutes) after `Date.now()`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Reuse an active pickup PIN
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-US-003</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that re-opening the PIN modal while a PIN is still active returns the same active PIN with its ongoing expiry instead of generating a new one. (Maps to TC-SRV-PIN-US-003)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Pickup PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Reservation `bb-001` with an active non-expired PIN (`pin IS NOT NULL AND expired_at > NOW()`), e.g. PIN `111111`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Generate a PIN, close the modal, then click "View PIN" again before expiry.</li>
          <li>Compare the two displayed PINs and countdown values.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">The same PIN (`111111`) and its remaining expiry are returned; no `UPDATE` writing a new PIN is executed (only 2 queries total).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Missing or invalid-status reservation rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-US-002 / TC-CTL-PIN-US-002</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that generating a PIN for a reservation that does not exist (or is not in `reserved`/`pending`) returns `RESERVATION_NOT_FOUND`. (Maps to TC-SRV-PIN-US-002 / TC-CTL-PIN-US-002)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Pickup PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">User `u-001` requesting a PIN for a non-existent or already-`borrowed` `borrow_id`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Attempt to generate a PIN for a reservation the user does not own or that has moved past `pending`.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 404 `{ code: "RESERVATION_NOT_FOUND", message: "Reservation not found or invalid status" }`; only the initial lookup query is executed.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: PIN collision retry exhaustion
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-US-004</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that when all 3 unique-constraint attempts (SQLSTATE 23505) fail, the system returns `PIN_GENERATION_FAILED` with HTTP 500 instead of crashing. (Maps to TC-SRV-PIN-US-004)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Pickup PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">A reservation where every generated candidate PIN collides with an existing active PIN (`UPDATE` throws code `23505` on all 3 attempts).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Force a unique-violation on each PIN generation attempt.</li>
          <li>Inspect the returned error.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 500 `{ code: "PIN_GENERATION_FAILED", message: "Failed to generate unique PIN after 3 attempts" }` (no uncaught exception).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Non-unique database errors are propagated
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-US-005</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that genuine database errors (e.g., connection lost) are not swallowed by the PIN retry loop and are rethrown. (Maps to TC-SRV-PIN-US-005)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Pickup PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">The PIN `UPDATE` throws `Error("connection lost")` (no `23505` code).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Simulate a connection failure during PIN persistence.</li>
          <li>Observe the resulting behavior.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">The `connection lost` error is rethrown (surfaces to the error-handling layer) and is not retried 3 times.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller returns generated PIN on success
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-PIN-US-001</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify the controller returns `{ success: true, data: { pin, expiresAt } }` when the service succeeds. (Maps to TC-CTL-PIN-US-001)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Pickup PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`req.user.userId = "u-001"`, `req.params.reservationId = "bb-001"`; service resolves `{ pin: "123456", expiresAt }`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Call the generate-PIN endpoint with a valid reservation.</li>
          <li>Inspect the JSON response body.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">`{ success: true, data: { pin: "123456", expiresAt } }`; no 4xx status returned.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller forwards domain error status code
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-PIN-US-002</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify the controller forwards service domain errors together with their status code. (Maps to TC-CTL-PIN-US-002)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Pickup PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Service resolves `{ error: { code: "RESERVATION_NOT_FOUND", message: "Reservation not found or invalid status" }, statusCode: 404 }`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Trigger a PIN generation for an invalid reservation.</li>
          <li>Inspect the response status and body.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 404 with `{ success: false, error: { code: "RESERVATION_NOT_FOUND", message: "Reservation not found or invalid status" } }`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller defaults to 400 for unknown error shape
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-PIN-US-003</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify the controller defaults to HTTP 400 when a service error has no `statusCode`. (Maps to TC-CTL-PIN-US-003)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Pickup PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Service resolves `{ error: { code: "X", message: "msg" } }` without `statusCode`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Force the service to return a bare error object.</li>
          <li>Inspect the HTTP status.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 400.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller returns 500 on unexpected throw
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-PIN-US-004</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify the controller returns `500 INTERNAL_ERROR` with a generic message when the service throws unexpectedly. (Maps to TC-CTL-PIN-US-004)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Pickup PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Service throws `Error("db down")`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Simulate an unexpected service exception.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 500 `{ success: false, error: { code: "INTERNAL_ERROR", message: "An unexpected error occurred" } }`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Cleanup resets reservation PIN and status
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-US-011 / TC-CTL-PIN-US-005</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that PIN cleanup clears `pin`/`expired_at` and restores the status to `reserved` for a `pending` row, returning `cleaned: true`. (Maps to TC-SRV-PIN-US-011 / TC-CTL-PIN-US-005)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Pickup PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Reservation `bb-001` in `pending` status with an expired PIN; cleanup call `cleanupReservationPin("u-001", "bb-001")`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Let a generated PIN expire (or trigger cleanup).</li>
          <li>Run the cleanup routine and inspect the database row.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Cleanup returns `true`; the row now has `pin = NULL`, `expired_at = NULL`, `status = 'reserved'`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Find borrow record by PIN
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-001</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that a borrow record matching a PIN is returned joined with the borrower (user) and book details. (Maps to TC-SRV-PIN-LIB-001)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Pickup PIN and Confirm Borrowing</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">PIN `123456` with status `pending`; a matching row exists in `public.borrow_book` joined with `users` and `books`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Query the borrow record by the PIN.</li>
          <li>Verify the joined user and book fields are present.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Returns the record containing `borrow_id`, `user_id`, `book_id`, `status`, plus user and book metadata.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: No record matches the PIN
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-002</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that looking up a PIN with no matching row returns `null`. (Maps to TC-SRV-PIN-LIB-002)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Pickup PIN and Confirm Borrowing</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">PIN `999999` with no matching `borrow_book` row.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Look up a non-existent PIN.</li>
          <li>Inspect the returned value.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Returns `null`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Valid pickup PIN returns borrower and book details
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-003 / TC-CTL-PIN-LIB-003</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that verifying a valid PIN at the correct branch returns the borrower identity and book details. (Maps to TC-SRV-PIN-LIB-003 / TC-CTL-PIN-LIB-003)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Pickup PIN and Confirm Borrowing</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">PIN `123456`, librarian branch 1; record `branch_id = 1`, status `pending`, book "Clean Code".</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>At the counter, enter the PIN provided by the member.</li>
          <li>Verify the confirmation screen shows the borrower and book.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Returns `{ borrowId, borrower: { username, gender, phone_number, email }, book: { title, author, publisher, genre, price } }`; controller responds `success: true` with message "PIN verified successfully".</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Invalid or expired PIN rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-004 / TC-CTL-PIN-LIB-011</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that an invalid or expired PIN returns `PIN_NOT_FOUND` with HTTP 404. (Maps to TC-SRV-PIN-LIB-004 / TC-CTL-PIN-LIB-011)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Pickup PIN and Confirm Borrowing</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">PIN `999999` (no row) or a PIN whose `expired_at` is in the past.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Enter a wrong or expired PIN at the counter.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 404 `{ code: "PIN_NOT_FOUND", message: "The PIN has expired or does not exist." }`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: PIN from another branch rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-005 / TC-CTL-PIN-LIB-004</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that verifying a PIN whose reservation belongs to another branch returns `WRONG_BRANCH` with HTTP 403. (Maps to TC-SRV-PIN-LIB-005 / TC-CTL-PIN-LIB-004)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Pickup PIN and Confirm Borrowing</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Librarian at branch 1 verifies PIN `123456` whose record has `branch_id = 2`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>At branch 1, enter a PIN generated for a reservation at branch 2.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 403 `{ code: "WRONG_BRANCH", message: "You have arrived at the wrong book borrowing branch." }`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller rejects malformed PIN format
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-PIN-LIB-001</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that a PIN that is not exactly 6 digits is rejected by the controller with HTTP 400 before calling the service. (Maps to TC-CTL-PIN-LIB-001)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Pickup PIN and Confirm Borrowing</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`req.body = { pin: "123" }` (3 digits).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Submit a short PIN at the verify endpoint.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 400; the verification service is not called.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Confirm borrowing sets status and due date
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-009 / TC-CTL-PIN-LIB-007</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that confirming borrowing sets `status = 'borrowed'`, `borrow_date = NOW()`, `due_date = NOW() + 14 days` and commits the transaction. (Maps to TC-SRV-PIN-LIB-009 / TC-CTL-PIN-LIB-007)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Pickup PIN and Confirm Borrowing</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`borrow_id = "bb-001"`, user eligible (no overdue books, account exists).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>After PIN verification, confirm the borrowing at the counter.</li>
          <li>Verify `BEGIN`/`COMMIT` executed and the row state.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">`{ borrowId, status: "borrowed", due_date }`; `COMMIT` executed; the SQL sets `due_date = NOW() + INTERVAL '14 days'`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Confirm borrowing on missing record rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-010</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that confirming a borrowing whose record does not exist returns `NOT_FOUND` and rolls back the transaction. (Maps to TC-SRV-PIN-LIB-010)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Pickup PIN and Confirm Borrowing</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">A `borrow_id` with no matching `borrow_book` row.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Attempt to confirm a borrowing that was already cancelled.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 404 `{ code: "NOT_FOUND", message: "Borrow record not found." }`; `ROLLBACK` executed.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Ineligible borrower rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-011 / TC-SRV-PIN-LIB-012 / TC-CTL-PIN-LIB-008</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that confirming a borrowing for a borrower with overdue books or a suspended/missing account returns `USER_INELIGIBLE` with HTTP 409 and rolls back. (Maps to TC-SRV-PIN-LIB-011 / TC-SRV-PIN-LIB-012 / TC-CTL-PIN-LIB-008)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Pickup PIN and Confirm Borrowing</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Borrower has `overdue_count = 2` (or no user row exists).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Attempt to confirm borrowing for a borrower with overdue books.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 409 `{ code: "USER_INELIGIBLE", message: "Borrower has overdue books or is suspended. Cannot confirm borrowing." }`; `ROLLBACK` executed.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller rejects missing borrow_id on confirmation
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-PIN-LIB-006</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify the controller returns HTTP 400 when `borrow_id` is missing in a confirm-borrowing request. (Maps to TC-CTL-PIN-LIB-006)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Pickup PIN and Confirm Borrowing</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`req.body = {}` (no `borrow_id`).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Send the confirm-borrowing request without `borrow_id`.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 400; the confirmation service is not called.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Generate a 6-digit return PIN
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-US-006</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that generating a return PIN for a currently `borrowed` book produces a 6-digit PIN and sets the status to `pending_return`. (Maps to TC-SRV-PIN-US-006)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Return PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">User `u-001`, borrow record `bb-001` in status `borrowed`; request with `borrow_id = "bb-001"`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>In the user dashboard, click the return-PIN button on a borrowed book card.</li>
          <li>Verify the modal shows a 6-digit code.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">PIN matches `/^\d{6}$/`; `borrow_book.status` = `pending_return`; the update query uses `[pin, expiresAt, borrow_id]`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Book not currently borrowed rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-US-007 / TC-CTL-PIN-US-009</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that generating a return PIN for a book that is not currently `borrowed` returns `BORROW_NOT_FOUND` with HTTP 404. (Maps to TC-SRV-PIN-US-007 / TC-CTL-PIN-US-009)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Return PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">A `borrow_id` with no row in status `borrowed`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Attempt to generate a return PIN for an already-returned or reserved book.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 404 `{ code: "BORROW_NOT_FOUND", message: "Borrow record not found or book is not currently borrowed" }`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Database failure returns 500
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-US-008</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that a database failure during return-PIN generation returns `INTERNAL_ERROR` with HTTP 500. (Maps to TC-SRV-PIN-US-008)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Return PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`pool.query` rejects with `Error("db down")`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Stop/block the database and attempt to generate a return PIN.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 500 `{ error: { code: "INTERNAL_ERROR", message: "db down" }, statusCode: 500 }`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Cleanup restores return status
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-US-009 / TC-CTL-PIN-US-010</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that return-PIN cleanup clears `pin`/`expired_at` and restores the status to `borrowed` when a `pending_return` row is updated. (Maps to TC-SRV-PIN-US-009 / TC-CTL-PIN-US-010)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Return PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Borrow record `bb-001` in `pending_return` with an expired return PIN.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Let the return PIN expire.</li>
          <li>Run cleanup and inspect the row.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Cleanup returns `true`; the SQL sets `pin = NULL, expired_at = NULL, status = 'borrowed'` for `[borrow_id, user_id]`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Cleanup returns false when nothing matched
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-US-010</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that cleanup returns `false` when no row matched the `pending_return` state. (Maps to TC-SRV-PIN-US-010)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Return PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`pool.query` resolves with `rowCount: 0`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Run cleanup for a record already past the `pending_return` state.</li>
          <li>Inspect the returned value.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Returns `false`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller rejects missing borrow_id
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-PIN-US-007</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify the controller returns HTTP 400 when `borrow_id` is missing in a return-PIN request. (Maps to TC-CTL-PIN-US-007)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Return PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`req.body = {}`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Send the return-PIN request without `borrow_id`.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 400; the return-PIN service is not called.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller returns generated return PIN on success
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-PIN-US-008</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify the controller returns the generated return PIN, its expiry, and a success message. (Maps to TC-CTL-PIN-US-008)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Return PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`req.body = { borrow_id: "bb-001" }`; service resolves `{ pin: "654321", expiresAt }`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Generate a return PIN for a borrowed book.</li>
          <li>Inspect the JSON response body.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">`{ success: true, data: { pin: "654321", expiresAt }, message: "Return PIN generated successfully" }`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller forwards BORROW_NOT_FOUND error
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-PIN-US-009</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify the controller forwards the `BORROW_NOT_FOUND` domain error with its 404 status. (Maps to TC-CTL-PIN-US-009)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Return PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`req.body = { borrow_id: "bb-001" }`; service resolves `{ error: { code: "BORROW_NOT_FOUND", message: "..." }, statusCode: 404 }`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Generate a return PIN for a book that is not currently borrowed.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 404 with `{ success: false, data: null, message: "Borrow record not found or book is not currently borrowed" }`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Cleanup controller returns cleaned status
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-PIN-US-010</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify the cleanup-return-PIN controller returns `{ success: true, cleaned: true }` when the cleanup succeeded. (Maps to TC-CTL-PIN-US-010)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Return PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`req.params.borrowId = "bb-001"`; cleanup service resolves `true`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Trigger cleanup for an expired return PIN.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">`{ success: true, cleaned: true }`; the service was called with `("u-001", "bb-001")`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Cleanup controller returns 500 on throw
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-PIN-US-011</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify the cleanup-return-PIN controller returns HTTP 500 when the cleanup service throws. (Maps to TC-CTL-PIN-US-011)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Generate Return PIN</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`req.params.borrowId = "bb-001"`; cleanup service throws `Error("boom")`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Trigger cleanup while the database is unavailable.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 500 (internal error).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Valid return PIN returns borrowing details
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-007 / TC-CTL-PIN-LIB-010</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that verifying a valid return PIN returns the borrower, book, and borrowing (dates) details. (Maps to TC-SRV-PIN-LIB-007 / TC-CTL-PIN-LIB-010)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Return PIN and Confirm Return</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Return PIN `654321`; record in status `pending_return` with `borrow_date` and `due_date` populated.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>At the counter, enter the return PIN provided by the member.</li>
          <li>Verify the return screen shows borrower, book, and due date.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Returns `{ borrowId, borrower, book, borrowing: { reserve_date, borrow_date, due_date } }`; the query matches `bb.pin = $1 AND bb.expired_at > NOW()`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Invalid return PIN rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-008 / TC-CTL-PIN-LIB-011</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that an invalid or expired return PIN returns `PIN_NOT_FOUND` with HTTP 404. (Maps to TC-SRV-PIN-LIB-008 / TC-CTL-PIN-LIB-011)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Return PIN and Confirm Return</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Return PIN `999999` (no matching row).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Enter a wrong or expired return PIN.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 404 `{ code: "PIN_NOT_FOUND", message: "The PIN has expired or does not exist." }`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Clean return recorded and inventory restored
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-014 / TC-CTL-PIN-LIB-013</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that confirming a clean return (perfect condition, no penalty) inserts a `return_book` row, restores inventory, decrements `borrow_num`, and commits. (Maps to TC-SRV-PIN-LIB-014 / TC-CTL-PIN-LIB-013)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Return PIN and Confirm Return</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`confirmReturn("bb-001", 1, ["perfect_condition"], null, false)`; book price 50.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Confirm the return of a book in perfect condition.</li>
          <li>Verify the return row, inventory, and borrow count in the database.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">`COMMIT` executed; `return_book` row inserted; `available_quantity` incremented by 1; `borrow_num` decremented via `GREATEST(borrow_num - 1, 0)`; returns `{ success: true, data: { returnId, penaltyId: null, penaltyAmount: 0, issue: null, inventoryUpdated: true } }`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Return for non-pending_return record rejected
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-015 / TC-CTL-PIN-LIB-015</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that confirming a return for a record not in `pending_return` returns `NOT_FOUND` and rolls back. (Maps to TC-SRV-PIN-LIB-015 / TC-CTL-PIN-LIB-015)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Return PIN and Confirm Return</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">A `borrow_id` whose record is not in `pending_return` status.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Attempt to confirm a return without a prior return PIN.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 404 `{ code: "NOT_FOUND", message: "Borrow record not found or not in pending_return status" }`; `ROLLBACK` executed.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Lost book charged twice the price
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-016</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that confirming a return for a lost book charges a penalty of twice the book price, records the penalty, and does not restore inventory. (Maps to TC-SRV-PIN-LIB-016)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Return PIN and Confirm Return</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`confirmReturn("bb-001", 1, [], "Book lost", true)`; book price 50.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Mark the returned book as lost and confirm the return.</li>
          <li>Verify the penalty amount and the `book_penalty` row.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">A `book_penalty` row is inserted; returns `{ success: true, data: { returnId: null, penaltyId: null, penaltyAmount: 100, issue: "lost", inventoryUpdated: false } }`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Damaged book penalty applied
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-017</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that a damaged book is charged a penalty based on the worst damage coefficient, and inventory is restored. (Maps to TC-SRV-PIN-LIB-017)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Return PIN and Confirm Return</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`confirmReturn("bb-001", 1, ["folded_pages"], "Fold corner", false)`; price 50; `folded_pages` coefficient 0.10 → 0.10 × 50 + admin fee = 6.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Inspect a returned book with folded pages and confirm the return.</li>
          <li>Verify the computed penalty.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">`penaltyAmount = 6`, `issue = "damaged"`, `inventoryUpdated = true`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Overdue return penalty charged
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-018</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that returning a book after the due date (even in perfect condition) charges an overdue penalty. (Maps to TC-SRV-PIN-LIB-018)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Return PIN and Confirm Return</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`borrow_date = 2026-07-01`, `due_date = 2026-07-10` (already past), price 100; return today.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Confirm the return of a book whose due date has passed.</li>
          <li>Verify the penalty.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">`issue = "overdue"` and `penaltyAmount > 0`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: PIN cleared after successful return
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-019</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that a successful return clears the PIN and expiry from the `borrow_book` row so the PIN cannot be reused. (Maps to TC-SRV-PIN-LIB-019)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Return PIN and Confirm Return</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Borrow record `bb-001` in `pending_return` status with a stored PIN.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Confirm the return of a book.</li>
          <li>Query the `borrow_book` row and verify the PIN fields.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">The SQL `UPDATE public.borrow_book SET pin = NULL, expired_at = NULL` is executed for `[borrow_id]`, so the PIN cannot be reused.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Transaction rollback and client release on failure
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-PIN-LIB-020</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that when the return transaction throws, the transaction is rolled back and the database client is released (no connection leak). (Maps to TC-SRV-PIN-LIB-020)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Return PIN and Confirm Return</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`confirmReturn("bb-001", 1, ["perfect_condition"], null, false)` where the borrow-record query throws `Error("transaction failed")`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Cause a database failure during the return transaction.</li>
          <li>Verify rollback and connection release.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">`ROLLBACK` executed, `client.release()` called exactly once, and the error `transaction failed` propagates.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller rejects missing confirm-return parameters
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-PIN-LIB-012</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify the controller returns HTTP 400 when `borrow_id` or `branch_id` is missing in a confirm-return request. (Maps to TC-CTL-PIN-LIB-012)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Verify Return PIN and Confirm Return</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">`req.body = { borrow_id: "bb-001" }` (no `branch_id`).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Send the confirm-return request without `branch_id`.</li>
          <li>Inspect the response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP 400; the confirm-return service is not called.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Nhựt Huy</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
  </tbody>
</table>

## VII. Create Study Group


<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Successful API creation
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-INT-CSG-001</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that the API returns 201 after the complete route pipeline normalizes and creates a group.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Valid payload with a valid Bearer token.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Send POST request to `/api/study-groups` with valid payload and token.</li>
          <li>Verify response status code.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Response status 201.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Add check for createdAt and groupId fields in the response payload.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Frontend requires these fields to display details immediately after creation.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Missing bearer token
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-INT-CSG-002</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that the API returns 401 when the bearer token is missing.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Request without Authorization header.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Send POST request to `/api/study-groups`.</li>
          <li>Observe response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Response status 401 with `AUTH_REQUIRED`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Return 401 with error code 'UNAUTHORIZED_ACCESS'.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Standardize security error codes according to the new global system guidelines.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Invalid token
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-INT-CSG-003</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that the API returns 401 when the token is invalid.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Invalid or malformed Bearer token.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Send POST request to `/api/study-groups` with invalid token.</li>
          <li>Observe response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Response status 401 with `INVALID_TOKEN`.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Return 401 with a detailed message: 'Token expired or malformed'.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Clarify the token error cause for easier debugging on the client side.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Unauthorized role guard
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-INT-CSG-004</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that the API returns 403 for non-student roles.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Token representing a librarian or admin user.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Send POST request with non-student role token.</li>
          <li>Observe response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Response status 403.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Return 403 Forbidden and log a security warning.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Security team requires auditing all unauthorized access attempts.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Request validation - unsupported field
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-INT-CSG-005</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that the API returns a structured 400 response for an unsupported field.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Payload containing the unsupported field `createdBy`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Send POST request with unsupported field.</li>
          <li>Observe response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Response status 400.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Return 400 Bad Request and explicitly list the invalid field name in the 'details' array.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Helps frontend easily parse the error and display an alert to the user.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Request validation - invalid metadata
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-INT-CSG-006</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that the API returns a structured 400 response for invalid creation metadata.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Payload containing `title: "12345"`, which has no letter.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Send POST request with invalid payload.</li>
          <li>Observe response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Response status 400.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Return 400 with a specific message about the malformed metadata format.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Improve API Developer Experience (DX) with clearer error messages.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Service outcome mapping (Not Found / Conflict)
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-INT-CSG-007</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that service-layer errors are mapped to appropriate HTTP status codes (404, 409).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Service layer rejects with `NOT_FOUND`, `SLOT_UNAVAILABLE`, or `INVALID_CAPACITY`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Trigger a service conflict error.</li>
          <li>Observe API response mapping.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Response status 404 or 409.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Check for an additional 409 Conflict error if the study group name already exists.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Ensure study group names are unique across the system.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Unexpected service failure (500)
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-INT-CSG-008</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that the API returns a safe 500 envelope for unexpected failures.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Simulated internal server error.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Force service to throw an unexpected error.</li>
          <li>Observe API response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Response status 500.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Return 500 along with a trace ID (if available).</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Facilitates faster system log tracing for internal errors.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Normalize a valid creation request</th></tr></thead>
  <tbody>
    <tr><td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-MID-CSG-001</strong></td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Verify that the middleware converts a numeric availability ID, trims metadata, and removes empty requirements before continuing.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Create Study Group</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">`availId: "12"` and metadata/requirements containing surrounding spaces and an empty item.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;"><ol style="margin: 0; padding-left: 20px; line-height: 1.6;"><li>Invoke `validateCreateStudyGroup` with the valid request.</li><li>Inspect the normalized body and middleware continuation.</li></ol></td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">`availId` becomes `12`, metadata is trimmed, empty requirements are removed, `next()` is called once, and no error response is sent.</td></tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Middleware calls next() and flags request.body with `isNormalized = true`.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Makes it easier to track the preprocessing state of the payload.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Default omitted requirements</th></tr></thead>
  <tbody>
    <tr><td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-MID-CSG-002</strong></td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Verify that omitted optional requirements default to an empty array.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Create Study Group</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">A valid creation request without the `requirements` field.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;"><ol style="margin: 0; padding-left: 20px; line-height: 1.6;"><li>Remove `requirements` from the valid request.</li><li>Invoke the creation middleware and inspect the request body.</li></ol></td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">`requirements` is `[]` and `next()` is called once.</td></tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Assign a null value to the requirements array instead of leaving it empty if omitted.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Saves bandwidth and standardizes default values in the database.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Reject an unsupported request field</th></tr></thead>
  <tbody>
    <tr><td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-MID-CSG-003</strong></td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Verify that the middleware rejects unsupported fields and reports their names.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Create Study Group</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">A valid request containing `createdBy: "another-user"`.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;"><ol style="margin: 0; padding-left: 20px; line-height: 1.6;"><li>Add `createdBy` to the request body.</li><li>Invoke the middleware and inspect the response.</li></ol></td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 400 with `VALIDATION_ERROR`, `Unsupported request field.`, and `details.fields: ["createdBy"]`; `next()` is not called.</td></tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Silently drop the invalid field instead of throwing an error.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Requirement change: apply strict pick mechanism instead of throwing errors.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Reject an invalid availability ID</th></tr></thead>
  <tbody>
    <tr><td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-MID-CSG-004</strong></td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Verify that the middleware rejects availability IDs that are not positive integers.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Create Study Group</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Parameterized values: `0`, `-1`, `1.5`, and `"not-a-number"`.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;"><ol style="margin: 0; padding-left: 20px; line-height: 1.6;"><li>Set each invalid value as `availId`.</li><li>Invoke the middleware and inspect each response.</li></ol></td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">Each value returns HTTP 400 with `VALIDATION_ERROR` and `availId must be a positive integer.`; `next()` is not called.</td></tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Return 422 Unprocessable Entity instead of 400.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Standardize HTTP status codes: use 422 for data logic errors.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Reject an invalid start date format</th></tr></thead>
  <tbody>
    <tr><td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-MID-CSG-005</strong></td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Verify that the middleware requires `startDate` to use `YYYY-MM-DD`.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Create Study Group</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">`startDate: "01/08/2099"`.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;"><ol style="margin: 0; padding-left: 20px; line-height: 1.6;"><li>Set the slash-formatted date in the request.</li><li>Invoke the middleware and inspect the response.</li></ol></td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 400 with `VALIDATION_ERROR` and `startDate must use YYYY-MM-DD.`; `next()` is not called.</td></tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Accept ISO-8601 format instead of only YYYY-MM-DD.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Support multiple time zones for international students.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead><tr style="background-color: #1e3a8a; color: #ffffff;"><th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">Test Case: Reject more than five normalized requirements</th></tr></thead>
  <tbody>
    <tr><td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td><td style="vertical-align: top;"><strong>TC-MID-CSG-006</strong></td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td><td style="vertical-align: top;">Verify that the middleware rejects more than five non-empty requirements after normalization.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td><td style="vertical-align: top;">Create Study Group</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td><td style="vertical-align: top;">Six non-empty requirements: `["1", "2", "3", "4", "5", "6"]`.</td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td><td style="vertical-align: top;"><ol style="margin: 0; padding-left: 20px; line-height: 1.6;"><li>Set six requirements in the request.</li><li>Invoke the middleware and inspect the response.</li></ol></td></tr>
    <tr><td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td><td style="vertical-align: top;">HTTP 400 with `VALIDATION_ERROR` and the five-item limit message; `next()` is not called.</td></tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Accept a maximum of 10 requirements instead of 5.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Lecturer feedback requested more conditions for large study groups.</td>
    </tr>
  </tbody>
</table>

**--- CONTROLLER LEVEL ---**

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller delegates correctly
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-CSG-001</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that the controller delegates the authenticated user and request body to the service layer.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Valid req and res objects.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke controller method.</li>
          <li>Spy on service invocation.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Controller forwards correct parameters to service.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Controller calls the service with a parameter containing the user's IP.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Required for the newly added rate-limiting feature.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller socket emission order
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-CSG-002</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that the controller emits the created socket event only after the service succeeds.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Valid req, res, and mocked socket layer.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke controller method successfully.</li>
          <li>Check socket emission order.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Socket event is emitted successfully after service completion.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Socket event is emitted with a payload format including the creator's details.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Frontend needs the creator's name to display a more detailed real-time notification.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller maps validation error
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-CSG-003</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that the controller maps a Study Group error to its status and complete error envelope.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Service throws mapped validation error.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke controller.</li>
          <li>Verify status and next() call.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Response status 400 with details.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Log validation errors to controller.log before returning the response.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Audit log requirement from the DevOps team.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Controller maps internal error
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-CTL-CSG-004</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify that the controller maps an unexpected failure to 500 without emitting an event.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Service throws generic error.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke controller method.</li>
          <li>Verify socket emission was skipped.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Response status 500.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Send an alert to the monitoring system (e.g., Sentry) before returning 500.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Ensure the operations team is notified immediately.</td>
    </tr>
  </tbody>
</table>

**--- SERVICE LEVEL ---**

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Metadata normalization
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-CSG-001</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify trimming of metadata and removal of empty requirements.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Metadata with extra spaces and empty array elements.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Call `normalizeMetadata`.</li>
          <li>Verify output.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Returns cleaned up payload.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Trim all special characters (e.g., tabs, newlines) from metadata.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Prevent UI rendering issues when users paste text from Word documents.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Requirements coercion
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-CSG-002</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Verify coercion of requirement values to strings before trimming.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Array containing numbers, booleans, and un-trimmed strings.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Call `normalizeRequirements`.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Returns an array of standard strings.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Coerce requirements to strings and limit each item to 100 characters.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Prevent memory overflow or UI breaking due to excessively long strings.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Unauthenticated rejection
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-CSG-003</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Rejects an unauthenticated caller before opening a transaction.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Null user ID.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke service.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Rejects with UNAUTHORIZED (401).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Throw an additional `UserNotFoundError` if the ID does not exist in the DB.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Prevent edge cases where an account is physically deleted but the token remains valid.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Invalid metadata rejection
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-CSG-004</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Rejects invalid metadata before opening a transaction.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Blank title, title without letters (`12345`), blank description, or subject without letters (`---`).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke service.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Rejects with VALIDATION_ERROR (400).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Add stricter XSS vulnerability checks in the study group description.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Mandatory requirement from the periodic security review.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Requirements overflow rejection
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-CSG-005</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Rejects more than five normalized requirements before opening a transaction.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Array with 6 requirements.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke service.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Rejects with VALIDATION_ERROR (400).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Change the error message to 'The number of requirements exceeds the allowed limit'.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Update the error message format based on new localization requirements.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Missing slot rejection
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-CSG-006</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Rejects a missing slot without inserting a reservation or group.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Non-existent slot.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke service.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Rejects with NOT_FOUND (404).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Return a list of available slots if the availId is invalid.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Improve user friendliness by suggesting options instead of just throwing an error.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Invalid capacity rejection
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-CSG-007</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Rejects a room with no host capacity without writing data.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Slot with capacity 0.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke service.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Rejects with INVALID_CAPACITY (409).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Verify the validity of the start time (must not be in the past).</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Prevent the creation of study groups with invalid historical timestamps.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Already-booked slot rejection
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-CSG-008</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Rejects an already-booked room slot before inserting a reservation or study group.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">The selected slot has capacity 4 and `occupied: true` for `availId: 12` on `2099-08-01`.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Mock the authoritative slot lookup to return an occupied slot.</li>
          <li>Invoke `createStudyGroup` with a valid payload.</li>
          <li>Verify that no reservation or study group insert is attempted.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Rejects with `SLOT_UNAVAILABLE` (409); `findSlotForCreation` receives availability ID, start date, and transaction client; no persistence insert runs.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Throw `CapacityError` if the expected member count exceeds room capacity.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Integrate with the library's facility management system.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Atomic creation orchestration
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-CSG-009</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Creates reservation then group and returns the projected detail in one transaction.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Valid payload.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke service.</li>
          <li>Verify transaction flow.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Returns group detail successfully.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Call transaction.rollback() explicitly in the catch block.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Ensure data integrity at the code level during unexpected failures.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Uniqueness race condition mapping
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-CSG-010</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Maps an active-slot uniqueness race to SLOT_UNAVAILABLE.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Database throws 23505 constraint error.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke service.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Rejects with SLOT_UNAVAILABLE (409).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Limit each user to creating a maximum of 3 groups per day.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Prevent spamming of fake study groups.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Auth user FK violation mapping
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-CSG-011</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Maps a missing authenticated user foreign key to AUTH_USER_NOT_FOUND.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Database throws fk violation for user.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke service.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Rejects with AUTH_USER_NOT_FOUND (401).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Validate an additional condition ensuring the user is not banned.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Integrate with the library management system's penalty feature.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Unexpected persistence error
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="22%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-CSG-012</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Preserves unexpected persistence errors for the controller boundary.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Create Study Group</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Generic Error instance.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke service.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Rejects with standard Error instance.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Nguyễn Lê Hoàng Khải</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Save the group creation history into the `audit_logs` table after a successful commit.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Support the user activity history retrieval feature.</td>
    </tr>
  </tbody>
</table>

## VIII. AI Recommendation

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: In-Memory Cache Hit Validation
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-REC-001</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Validate that repeating a recommendation request for an active user hits the in-memory Map cache (<code>recommendationCache</code>) and avoids secondary database SQL queries (<code>pool.query</code>).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">View Recommended Book (UC-AIR-01)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;"><code>userId = "test-user-id"</code>, memory cache pre-cleared, PostgreSQL DB containing 15 pre-computed recommendations.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Call <code>getUserRecommendations('test-user-id')</code>.</li>
          <li>Record the number of SQL queries executed by <code>pool.query</code>.</li>
          <li>Immediately invoke <code>getUserRecommendations('test-user-id')</code> a second time.</li>
          <li>Compare output objects and inspect <code>pool.query</code> call count.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">The first call queries the database once (<code>pool.query</code> count = 1) and returns 15 recommendation items. The second call retrieves the array directly from the in-memory Map cache (<code>pool.query</code> count remains 1). Returned array matching <code>result1 === result2</code>.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Trần Lê Hoàng Gia.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">N/A.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Database Connection Resilience & Catalog Fallback
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-REC-003</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Validate system fault tolerance when PostgreSQL pool encounters connection failure, verifying graceful fallback to standard catalog trend items without unhandled exceptions.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">View Recommended Book (UC-AIR-01)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;"><code>userId = "test-user-id"</code>, primary query configured to throw <code>Error('PostgreSQL Connection Failed')</code>, secondary query returning 15 fallback catalog books.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Execute <code>getUserRecommendations('test-user-id')</code> during active database pool exception.</li>
          <li>Capture returned data structure and inspect error handling logs.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Service handles exception internally without crashing or throwing an unhandled rejection. Returns exactly 15 fallback items with default <code>score: 0.0</code> and fallback titles (<code>fallback-book-0</code> through <code>fallback-book-14</code>).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Trần Lê Hoàng Gia.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">N/A.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: TCP Socket Inference Handler & Framing
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-REC-004</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Validate raw TCP socket IPC communication with Python ML micro-ranker daemon, verifying JSON payload framing with trailing newline <code>\n</code> and output score re-ranking.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">View Recommended Book (UC-AIR-01)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;"><code>userId = "test-user-id"</code>, Mock TCP Server on <code>127.0.0.1:5999</code> returning JSON payload with GCN scores <code>[0.9, 0.85, ...]</code>.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Trigger <code>generateRecommendations('test-user-id')</code>.</li>
          <li>Mock server intercepts JSON TCP payload containing candidate array and responds with score JSON.</li>
          <li>Validate candidate score ordering in service response.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Payload serialized as valid JSON string with trailing newline <code>\n</code>. Service receives and parses response buffer correctly. Recommendations returned sorted in descending order of GCN score (<code>result[0].score === 0.9</code>).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Trần Lê Hoàng Gia.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">N/A.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Memgraph Candidate Retrieval & Cold-Start Fallback
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-REC-005</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Validate candidate retrieval from Memgraph DB; verify that if primary graph traversal returns fewer than 60 records, secondary cold-start Cypher query is executed.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">View Recommended Book (UC-AIR-01)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;"><code>userId = "test-user-id"</code>, primary Cypher graph query yielding 5 records (&lt; 60 threshold), secondary cold-start query yielding 60 records.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Mock <code>getSession().run</code> to return 5 records on 1st call, and 60 records on 2nd call.</li>
          <li>Invoke <code>generateRecommendations('test-user-id')</code>.</li>
          <li>Count total calls to <code>session.run</code>.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;"><code>session.run</code> is executed exactly twice, successfully triggering the secondary cold-start graph traversal Cypher query. Candidate pool is populated with merged items from both graph passes.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Trần Lê Hoàng Gia.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">N/A.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Hard Guardrail – Out-of-Stock Item Filtering
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-REC-006</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Validate business rule inventory guardrail (<code>adjustCandidateScores</code>) ensuring items with 0 available physical copies (<code>global_available_copies === 0</code>) are pruned regardless of GCN score.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">View Recommended Book (UC-AIR-01)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Candidate <code>stock-book-0</code> with raw GCN score <code>0.9</code> and <code>global_available_copies: 0</code>; items <code>stock-book-1..14</code> with <code>global_available_copies: 5</code>.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Invoke <code>generateRecommendations('test-user-id')</code>.</li>
          <li>Inspect candidate list returned by service routine.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Candidate <code>stock-book-0</code> is completely pruned from recommendation output (<code>result.some(b =&gt; b.id === 'stock-book-0') === false</code>). Total returned items maintain quota via supplementation.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Trần Lê Hoàng Gia.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Adjusted output assertion to ensure 15 items are maintained via supplementation when out-of-stock items are pruned.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Clarified inventory guardrail replenishment requirement.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Exponential Skip Penalty Scoring Calculation
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-REC-007</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Validate mathematical precision of exponential skip decay formula Score_final = Score_GCN * (0.65)^N for past skipped impressions.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">View Recommended Book (UC-AIR-01)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;"><code>book-skipped</code> with raw score <code>0.90</code> and <code>past_impressions_count = 2</code>; <code>book-fresh</code> with raw score <code>0.80</code> and <code>past_impressions_count = 0</code>.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Execute <code>generateRecommendations('test-user-id')</code>.</li>
          <li>Extract calculated <code>book-skipped</code> score from output.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Final score matches exact mathematical formula: 0.90 * (0.65)^2 = 0.90 * 0.4225 = 0.38025. <code>expect(skippedItem.score).toBeCloseTo(0.38025, 4)</code> evaluates to true.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Trần Lê Hoàng Gia.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">N/A.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Candidate Pool Catalog Supplementation
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-REC-008</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Validate catalog supplementation algorithm ensuring recommendation feed strictly maintains minimum 15-item quota when graph queries return insufficient items.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">View Recommended Book (UC-AIR-01)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;"><code>userId = "test-user-id"</code>, Graph queries return only 1 item (<code>few-book-1</code>).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Execute <code>generateRecommendations('test-user-id')</code>.</li>
          <li>Check database queries for catalog supplementation pass.</li>
          <li>Verify returned array length.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Database is queried for catalog supplementation (<code>supp-book-0</code> through <code>supp-book-13</code>). Returned array length is exactly 15 items.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Trần Lê Hoàng Gia.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">N/A.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Click Tracking, Eviction & Graph Sync Integration
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-REC-009</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Validate end-to-end click tracking lifecycle: updating PostgreSQL click flag (<code>is_clicked = TRUE</code>), evicting user cache Map, and invoking async graph sync (<code>syncRecommendationClick</code>).</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">View Recommended Book (UC-AIR-01)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;"><code>userId = "test-user-id"</code>, <code>bookId = "book-0"</code>, active recommendations cached in memory Map.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Call <code>getUserRecommendations('test-user-id')</code> to populate cache.</li>
          <li>Invoke <code>logRecommendationClick('test-user-id', 'book-0')</code>.</li>
          <li>Assert PostgreSQL update query executed (<code>is_clicked = TRUE</code>).</li>
          <li>Assert <code>syncRecommendationClick</code> called with user, book ID, and timestamp.</li>
          <li>Call <code>getUserRecommendations('test-user-id')</code> again.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Click recorded successfully (<code>logged === true</code>). In-memory cache for user is evicted; subsequent lookup triggers DB reload (<code>pool.query</code> count increments). Non-blocking graph edge sync invoked with ISO timestamp.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No — split after baseline.</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Trần Lê Hoàng Gia.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">Adjusted expected output to check async graph sync non-blocking execution order and ISO timestamp format.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">Isolated graph edge sync integration scenario.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Express Controller API Contract Validation
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-REC-010</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Validate REST controller endpoint (<code>getRecommendations</code>) payload formatting into <code>historyBased</code> (15 items) and <code>trending</code> arrays with HTTP 200 OK status.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">View Recommended Book (UC-AIR-01) &amp; Reset AI Recommend (UC-AIR-02)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Mock Request <code>req = { user: { userId: 'test-user-id' } }</code>, Mock Response <code>res</code> with spied <code>json</code> and <code>status</code> methods.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Call <code>getRecommendations(req, res)</code> controller handler.</li>
          <li>Inspect response payload passed to <code>res.json()</code>.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP Response status implicitly set to 200 OK. Response payload contains <code>{ success: true, data: { historyBased: [...], trending: [...] } }</code>.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No — added after baseline.</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Trần Lê Hoàng Gia.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">N/A.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Cache Invalidation & Miss Flow
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-REC-002</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Validate that invoking <code>invalidateUserRecommendationCache</code> properly evicts user cache entry from memory Map, causing subsequent requests to trigger a database query miss.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">Reset AI Recommend (UC-AIR-02)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;"><code>userId = "test-user-id"</code>, active recommendations cached in memory Map.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Execute <code>getUserRecommendations('test-user-id')</code> to ensure cache populate (<code>pool.query</code> count = 1).</li>
          <li>Invoke <code>invalidateUserRecommendationCache('test-user-id')</code>.</li>
          <li>Call <code>getUserRecommendations('test-user-id')</code> once more.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">Cache eviction function succeeds silently. The subsequent <code>getUserRecommendations</code> call experiences a cache miss and queries PostgreSQL (<code>pool.query</code> count increments to 2).</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Trần Lê Hoàng Gia.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">N/A.</td>
    </tr>
  </tbody>
</table>

<table width="100%" border="1" cellpadding="8" cellspacing="0" style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px; border: 1px solid #d1d5db; margin-bottom: 20px;">
  <thead>
    <tr style="background-color: #1e3a8a; color: #ffffff;">
      <th colspan="2" style="text-align: left; padding: 12px; font-size: 16px;">
        Test Case: Express Controller API Contract Validation
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td width="24%" style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Case ID</td>
      <td style="vertical-align: top;"><strong>TC-SRV-REC-010</strong></td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Description</td>
      <td style="vertical-align: top;">Validate REST controller endpoint (<code>getRecommendations</code>) payload formatting into <code>historyBased</code> (15 items) and <code>trending</code> arrays with HTTP 200 OK status.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Related Use Case</td>
      <td style="vertical-align: top;">View Recommended Book (UC-AIR-01) &amp; Reset AI Recommend (UC-AIR-02)</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Input Data</td>
      <td style="vertical-align: top;">Mock Request <code>req = { user: { userId: 'test-user-id' } }</code>, Mock Response <code>res</code> with spied <code>json</code> and <code>status</code> methods.</td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Test Steps</td>
      <td style="vertical-align: top;">
        <ol style="margin: 0; padding-left: 20px; line-height: 1.6;">
          <li>Call <code>getRecommendations(req, res)</code> controller handler.</li>
          <li>Inspect response payload passed to <code>res.json()</code>.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="background-color: #f8fafc; font-weight: bold; vertical-align: top;">Expected Output</td>
      <td style="vertical-align: top;">HTTP Response status implicitly set to 200 OK. Response payload contains <code>{ success: true, data: { historyBased: [...], trending: [...] } }</code>.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Spec Kit Created</td>
      <td style="vertical-align: top;">No — added after baseline.</td>
    </tr>
    <tr> 
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed</td>
      <td style="vertical-align: top;">Yes.</td>
    </tr>
    <tr>
      <td style="background-color: #eef2ff; font-weight: bold; vertical-align: top;">Reviewed By</td>
      <td style="vertical-align: top;">Trần Lê Hoàng Gia.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Expected Result</td>
      <td style="vertical-align: top;">None.</td>
    </tr>
    <tr>
      <td style="background-color: #fff7ed; font-weight: bold; vertical-align: top;">Adjust Reason</td>
      <td style="vertical-align: top;">N/A.</td>
    </tr>
  </tbody>
</table>
