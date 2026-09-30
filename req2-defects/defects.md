# Tổng hợp 20 Software Defects / AI Incidents công bố trong giai đoạn 2022–2026

> **Phạm vi:** 5 sự cố/lỗ hổng liên quan AI/LLM (hallucination, prompt injection, model bias) và 15 software defects/lỗ hổng phần mềm thông thường.
>
> **Lưu ý về Severity:** Điểm CVSS đã được đối chiếu với NVD API ngày 30/09/2026 (trừ điểm CVSS v4 của GitHub Advisory chưa đối chiếu). Khi NVD và đơn vị cấp CVE/vendor chấm khác nhau thì ghi cả hai, kèm nguồn. Nếu có CVSS chính thức từ CVE/NVD/vendor thì tài liệu dùng điểm đó. Với các incident không có CVE/CVSS (Air Canada, Meta Housing Ads, CrowdStrike Channel File 291), mức Low/Medium/High/Critical được ghi là **đánh giá tác động kỹ thuật/vận hành**, không phải CVSS chính thức.

---

## Mục lục

1. [LangChain LLMMathChain – CVE-2023-29374](#1-langchain-llmmathchain--cve-2023-29374)
2. [Vanna.AI Prompt Injection to RCE – CVE-2024-5565](#2-vannaai-prompt-injection-to-rce--cve-2024-5565)
3. [EmailGPT Prompt Injection – CVE-2024-5184](#3-emailgpt-prompt-injection--cve-2024-5184)
4. [Air Canada Bereavement Chatbot – incorrect policy response](#4-air-canada-bereavement-chatbot--incorrect-policy-response)
5. [Meta Housing Ad Delivery – algorithmic bias](#5-meta-housing-ad-delivery--algorithmic-bias)
6. [Spring4Shell – CVE-2022-22965](#6-spring4shell--cve-2022-22965)
7. [Microsoft Follina / MSDT – CVE-2022-30190](#7-microsoft-follina--msdt--cve-2022-30190)
8. [Microsoft Outlook NTLM credential leak – CVE-2023-23397](#8-microsoft-outlook-ntlm-credential-leak--cve-2023-23397)
9. [MOVEit Transfer SQL Injection – CVE-2023-34362](#9-moveit-transfer-sql-injection--cve-2023-34362)
10. [Cisco IOS XE Web UI privilege escalation – CVE-2023-20198](#10-cisco-ios-xe-web-ui-privilege-escalation--cve-2023-20198)
11. [libwebp heap buffer overflow – CVE-2023-4863](#11-libwebp-heap-buffer-overflow--cve-2023-4863)
12. [GitLab password-reset account takeover – CVE-2023-7028](#12-gitlab-password-reset-account-takeover--cve-2023-7028)
13. [Atlassian Confluence Broken Access Control – CVE-2023-22515](#13-atlassian-confluence-broken-access-control--cve-2023-22515)
14. [glibc Looney Tunables – CVE-2023-4911](#14-glibc-looney-tunables--cve-2023-4911)
15. [XZ Utils supply-chain backdoor – CVE-2024-3094](#15-xz-utils-supply-chain-backdoor--cve-2024-3094)
16. [Palo Alto PAN-OS GlobalProtect command injection – CVE-2024-3400](#16-palo-alto-pan-os-globalprotect-command-injection--cve-2024-3400)
17. [Check Point Security Gateway information disclosure – CVE-2024-24919](#17-check-point-security-gateway-information-disclosure--cve-2024-24919)
18. [PHP-CGI Windows argument injection – CVE-2024-4577](#18-php-cgi-windows-argument-injection--cve-2024-4577)
19. [OpenSSH regreSSHion – CVE-2024-6387](#19-openssh-regresshion--cve-2024-6387)
20. [CrowdStrike Falcon Channel File 291 outage](#20-crowdstrike-falcon-channel-file-291-outage)

Phần C — [AI thiên lệch / hallucinate khi giải thích lỗi](#phần-c--chỗ-ai-thiên-lệch--hallucinate-khi-giải-thích-lỗi) · Phụ lục — [case AI dự phòng](#phụ-lục--case-ai-dự-phòng-không-tính-trong-20-case)

---

## Bảng tổng hợp nhanh

| #   | Defect / Incident                       |                  Năm công bố | Nhóm lỗi                                                  | Severity                                                        |
| --- | --------------------------------------- | ---------------------------: | --------------------------------------------------------- | --------------------------------------------------------------- |
| 1   | LangChain LLMMathChain – CVE-2023-29374 |                         2023 | Prompt Injection / Code Injection                         | Critical, CVSS v3.1 9.8 (NVD)                                   |
| 2   | Vanna.AI – CVE-2024-5565                |                         2024 | Prompt Injection → RCE                                    | High 8.1 (v3.1, JFrog); v4 Critical theo GitHub, chưa đối chiếu |
| 3   | EmailGPT – CVE-2024-5184                |                         2024 | Prompt Injection                                          | High 8.5 v4 / Medium 6.5 v3.1 (CNA); Critical 9.1 v3.1 (NVD)    |
| 4   | Air Canada chatbot                      | 2024 decision; incident 2022 | Incorrect generated response / hallucination-like failure | Medium\*                                                        |
| 5   | Meta Housing Ads                        |                         2022 | Model / Algorithmic Bias                                  | High\*                                                          |
| 6   | Spring4Shell – CVE-2022-22965           |                         2022 | Data Binding → RCE                                        | Critical 9.8                                                    |
| 7   | Follina – CVE-2022-30190                |                         2022 | Protocol handler / RCE                                    | High 7.8                                                        |
| 8   | Outlook – CVE-2023-23397                |                         2023 | NTLM credential leak / EoP                                | Critical 9.8                                                    |
| 9   | MOVEit – CVE-2023-34362                 |                         2023 | SQL Injection                                             | Critical 9.8                                                    |
| 10  | Cisco IOS XE – CVE-2023-20198           |                         2023 | Broken Access Control / Privilege Escalation              | Critical 10.0                                                   |
| 11  | libwebp – CVE-2023-4863                 |                         2023 | Heap Buffer Overflow                                      | High 8.8                                                        |
| 12  | GitLab – CVE-2023-7028                  |                         2024 | Password Recovery Logic Flaw                              | Critical 10.0 (GitLab) / 9.8 (NVD)                              |
| 13  | Confluence – CVE-2023-22515             |                         2023 | Broken Access Control                                     | Critical 10.0 (Atlassian, v3.0) / 9.8 (NVD v3.1)                |
| 14  | glibc Looney Tunables – CVE-2023-4911   |                         2023 | Buffer Overflow / Local Privilege Escalation              | High 7.8                                                        |
| 15  | XZ Utils – CVE-2024-3094                |                         2024 | Supply-chain / Embedded Malicious Code                    | Critical 10.0                                                   |
| 16  | PAN-OS – CVE-2024-3400                  |                         2024 | Command Injection                                         | Critical 10.0                                                   |
| 17  | Check Point – CVE-2024-24919            |                         2024 | Information Disclosure / Path Traversal-like file read    | High 8.6                                                        |
| 18  | PHP-CGI – CVE-2024-4577                 |                         2024 | Argument / OS Command Injection                           | Critical 9.8                                                    |
| 19  | OpenSSH regreSSHion – CVE-2024-6387     |                         2024 | Signal-handler Race Condition → RCE                       | High 8.1                                                        |
| 20  | CrowdStrike Channel File 291            |                         2024 | Validation defect / OOB memory read / outage              | Critical operational impact\*                                   |

\* Không phải CVSS chính thức.

---

# Phần A — 5 AI/LLM-related defects

## 1. LangChain `LLMMathChain` – CVE-2023-29374

### Defect name

**LangChain `LLMMathChain` Prompt Injection / Code Injection — CVE-2023-29374**

**Affected product:** LangChain `<= 0.0.131`.

### Source links

- GitHub Advisory: https://github.com/advisories/GHSA-fprp-p869-w6q2
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2023-29374

### Description

`LLMMathChain` được thiết kế để cho LLM tạo biểu thức/code phục vụ tính toán toán học. Vấn đề kiến trúc nằm ở chỗ output do mô hình sinh ra có thể đi tới Python `exec()`.

Data flow nguy hiểm có dạng:

```text
Untrusted user input
        ↓
Prompt
        ↓
LLM
        ↓
LLM-generated Python
        ↓
exec(...)
        ↓
Application process / OS
```

Vì input của người dùng có thể ảnh hưởng output của LLM, attacker có thể dùng **prompt injection** để làm mô hình sinh Python code ngoài mục đích tính toán. Khi output này được thực thi bằng `exec()`, ranh giới giữa **data** và **code** bị phá vỡ.

Root cause không phải đơn thuần là “LLM trả lời sai”, mà là lỗi thiết kế:

```text
probabilistic, attacker-influenced output
                ↓
        trusted code execution
```

Một natural-language instruction như “chỉ trả về phép toán” không phải security boundary. Model có thể bị điều khiển hoặc sinh output ngoài format mong đợi.

### Severity

NVD (đối chiếu qua NVD API ngày 30/09/2026):

- **Critical**
- **CVSS v3.1: 9.8** (`CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H`)

GitHub Advisory có thể hiển thị thang điểm CVSS v4 khác; điểm v4 không được đối chiếu ở đây nên báo cáo dùng điểm của NVD.

### Consequences

Nếu exploit thành công, attacker có thể thực thi code trong context của process chạy LangChain. Tùy quyền của process, attacker có khả năng:

- đọc file cấu hình;
- lấy environment variables;
- đánh cắp API key / database credential;
- sửa/xóa dữ liệu;
- thực hiện outbound network requests;
- pivot sang các internal services.

Một chatbot-level input defect vì vậy có thể chuyển thành **server compromise**.

### Solution

Biện pháp đúng về software architecture là loại bỏ đường đi trực tiếp:

```text
LLM output → exec()
```

Thay bằng:

```text
LLM output
   ↓
strict parser / schema validation
   ↓
allowlisted operation
   ↓
restricted execution
```

Đối với bài toán tính toán, chỉ nên cho phép AST hoặc grammar giới hạn như số, toán tử và hàm toán học xác định trước. Nếu bắt buộc chạy code sinh bởi model, cần sandbox, no-network, filesystem giới hạn, resource limits và account least privilege.

---

## 2. Vanna.AI Prompt Injection to RCE – CVE-2024-5565

### Defect name

**Vanna.AI Prompt Injection leading to Remote Code Execution — CVE-2024-5565**

### Source links

- JFrog Research: https://jfrog.com/blog/prompt-injection-attack-code-execution-in-vanna-ai-cve-2024-5565/
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2024-5565

### Description

Vanna.AI hỗ trợ text-to-SQL. Flow điển hình:

```text
Natural-language question
        ↓
LLM generates SQL
        ↓
Database
        ↓
DataFrame
        ↓
LLM generates Plotly Python code
        ↓
exec()
```

Khi visualization được bật, hệ thống dùng LLM để sinh Plotly code từ question, SQL và metadata. Code này sau đó được thực thi bằng Python.

Điểm nguy hiểm là dữ liệu attacker kiểm soát có thể được đưa qua nhiều stage:

```text
attacker question
      ↓
SQL generation
      ↓
SQL/result
      ↓
second LLM prompt
      ↓
generated Python
      ↓
exec()
```

Đây là ví dụ rõ của **cross-component taint propagation**: untrusted data không chỉ đi qua một function mà lan từ user input → SQL layer → prompt layer → code execution layer.

Prompt constraints kiểu “return only Plotly code” không có tính chất enforcement. Nếu model bị injection, attacker có thể khiến nó sinh Python không thuộc plotting logic.

### Severity

- **CVSS v3.1: 8.1 — High** (JFrog, đơn vị cấp CVE; NVD chưa có điểm riêng)
- GitHub Advisory ghi thêm mức **Critical** theo CVSS v4 (9.2); điểm v4 chưa được đối chiếu.

### Consequences

Attacker có thể đạt arbitrary Python code execution trong process Vanna:

- đọc file và secret;
- lấy DB credentials;
- truy vấn/sửa database;
- chạy OS commands;
- gọi internal network;
- thực hiện lateral movement.

Do Vanna thường được triển khai gần database, RCE có thể biến thành database compromise.

### Solution

Không nên cho LLM sinh Python tùy ý rồi `exec()`.

Thiết kế tốt hơn:

```text
LLM
 ↓
declarative chart specification
 ↓
schema validator
 ↓
trusted renderer
```

Ví dụ model chỉ được trả:

```json
{
  "chart": "bar",
  "x": "month",
  "y": "revenue"
}
```

Trusted application code sẽ convert cấu trúc trên thành Plotly calls.

Nếu vẫn phải thực thi code, cần AST validation, import allowlist, API allowlist, sandbox, no-network và least privilege.

---

## 3. EmailGPT Prompt Injection – CVE-2024-5184

### Defect name

**Prompt Injection in EmailGPT — CVE-2024-5184**

### Source links

- CVE.org: https://www.cve.org/CVERecord?id=CVE-2024-5184
- Synopsys advisory: https://www.synopsys.com/blogs/software-security/cyrc-advisory-prompt-injection-emailgpt.html

### Description

EmailGPT cho attacker đưa direct prompt vào AI service và làm thay đổi service logic. CVE ghi nhận attacker có thể ép hệ thống:

- leak hard-coded system prompts;
- thực thi các prompt ngoài mục đích thiết kế.

Kiến trúc rủi ro:

```text
system instructions
      +
application prompt
      +
untrusted user text
        ↓
       LLM
```

Nếu security policy chỉ tồn tại dưới dạng natural-language system prompt, chính model được giao nhiệm vụ “bảo vệ” policy đồng thời cũng là component phải parse untrusted natural language.

Đây là sự trộn lẫn giữa **control plane** và **data plane**.

### Severity

CVE.org ghi:

- **CVSS v4: 8.5 — High**
- **CVSS v3.1: 6.5 — Medium**

NVD (Primary) lại chấm **CVSS v3.1: 9.1 — Critical**. Khác biệt này đến từ việc hai đơn vị (Synopsys CNA và NVD) đánh giá khác nhau, không chỉ do khác phiên bản CVSS. Vì vậy báo cáo nêu cả ba điểm và nguồn của từng điểm.

### Consequences

Hậu quả trực tiếp:

- disclosure system prompts;
- lộ workflow/instruction nội bộ;
- model thực hiện task ngoài intended scope.

Trong agentic application, tác động có thể lớn hơn nếu model có quyền gọi tool như email, database hay external API.

### Solution

Không dùng prompt làm access-control mechanism.

Kiến trúc an toàn:

```text
LLM proposes action
       ↓
deterministic policy engine
       ↓
authentication / authorization
       ↓
schema + argument validation
       ↓
tool execution
```

Ngoài ra:

- không lưu secret trong prompt;
- giới hạn tool permissions;
- validate tất cả model-generated arguments;
- tách untrusted content khỏi control instructions;
- log và giám sát prompt injection patterns.

---

## 4. Air Canada Bereavement Chatbot – incorrect policy response

### Defect name

**Air Canada Bereavement-Fare Chatbot Incorrect Policy Response — Moffatt v. Air Canada, 2024 BCCRT 149**

### Source links

- Bản án (CanLII): https://www.canlii.org/en/bc/bccrt/doc/2024/2024bccrt149/2024bccrt149.html
- CanLII blog thảo luận bản án: https://blog.canlii.org/2024/03/

### Description

Khách hàng hỏi chatbot của Air Canada về bereavement fare. Chatbot nói rằng người dùng có thể mua vé thông thường, đi chuyến bay rồi yêu cầu áp dụng bereavement rate trong một khoảng thời gian sau đó.

Thông tin này không khớp với policy thật của Air Canada.

**Lưu ý kỹ thuật quan trọng:** hồ sơ công khai không mô tả model/architecture của chatbot, vì vậy không nên khẳng định chắc chắn đây là GPT/LLM hallucination. Nó phù hợp để phân tích dưới góc **hallucination-like / incorrect generated response**, nhưng nguyên nhân model cụ thể chưa được công khai.

Software-quality failure có thể mô tả là:

```text
chatbot-generated answer
          ≠
authoritative business policy
```

Root architecture problem là hệ thống không đảm bảo rằng câu trả lời thuộc high-impact business rule được lấy từ canonical source of truth.

### Severity

Không có CVSS.

**Đánh giá: Medium**

Lý do: không dẫn tới server compromise, nhưng tác động trực tiếp tới quyết định tài chính của khách hàng và gây liability pháp lý cho doanh nghiệp.

### Consequences

- người dùng ra quyết định mua vé dựa trên thông tin sai;
- phát sinh thiệt hại tài chính;
- tranh chấp;
- Air Canada bị tribunal xác định chịu trách nhiệm đối với thông tin chatbot trên website;
- ảnh hưởng uy tín và trust.

### Solution

Không để generative layer tự “nhớ” policy.

Thiết kế phù hợp:

```text
User question
     ↓
intent detection
     ↓
canonical policy service / DB
     ↓
deterministic eligibility result
     ↓
LLM only rephrases result
```

Với RAG, cần:

- retrieve canonical document;
- citation đến exact policy;
- confidence/grounding checks;
- fallback to human agent nếu không tìm được authoritative answer.

---

## 5. Meta Housing Ad Delivery – algorithmic bias

### Defect name

**Meta/Facebook Housing Advertisement Delivery Algorithm — discriminatory / biased delivery**

### Source links

- U.S. Department of Justice case: https://www.justice.gov/crt/case/united-states-v-meta-platforms-inc-fka-facebook-inc-sdny
- DOJ 2022 settlement announcement: https://www.justice.gov/archives/opa/pr/justice-department-secures-groundbreaking-settlement-agreement-meta-platforms-formerly-known
- Meta VRS technical overview: https://ai.meta.com/blog/advertising-fairness-variance-reduction-system-vrs/

### Description

DOJ alleged rằng hệ thống targeting/delivery quảng cáo nhà ở của Meta sử dụng algorithms có thể dựa một phần vào các đặc trưng liên quan đến protected classes, dẫn đến khác biệt giữa:

```text
Eligible Audience
       ↓
ML ranking / ad auction
       ↓
Actual Audience
```

Một model tối ưu cho click/conversion có thể học proxy features từ location, interests, activity, browsing behavior hoặc các signals tương quan với protected attributes.

Do đó việc “xóa field race/gender” chưa đủ:

```text
protected characteristic
      ↕ correlation
proxy features
      ↓
prediction/ranking
      ↓
unequal exposure
```

Đây là dạng **objective-function mismatch**: hệ thống tối ưu engagement/value nhưng không tự đảm bảo fairness constraint.

### Severity

Không áp dụng CVSS.

**Đánh giá tác động: High**

Housing là high-impact domain, hệ thống vận hành ở quy mô rất lớn và issue dẫn tới federal litigation, settlement và thay đổi core ad-delivery architecture.

### Consequences

- các nhóm người dùng khác nhau có thể nhận mức exposure không tương đương với housing opportunities;
- disparate impact ở quy mô hệ thống;
- rủi ro pháp lý;
- mất trust;
- phải thay đổi thuật toán và chịu court oversight.

### Solution

Meta ngừng **Special Ad Audience** cho housing và triển khai **Variance Reduction System (VRS)**.

VRS dùng feedback loop:

```text
Eligible demographic distribution
           ↓
       compare
           ↑
Actual impression distribution
           ↓
     variance metric
           ↓
control / pacing adjustment
           ↓
        ad auction
```

Mục tiêu là làm actual audience gần eligible audience hơn theo aggregate demographic distribution, đồng thời dùng privacy-enhancing measurement thay vì đưa protected attributes cá nhân trực tiếp vào controller.

---

# Phần B — 15 software defects/lỗ hổng bổ sung

## 6. Spring4Shell – CVE-2022-22965

### Defect name

**Spring Framework Data Binding Remote Code Execution (“Spring4Shell”) — CVE-2022-22965**

### Source links

- NVD: https://nvd.nist.gov/vuln/detail/CVE-2022-22965
- Spring advisory: https://spring.io/security/cve-2022-22965

### Description

Lỗ hổng nằm trong cơ chế **data binding** của Spring MVC/WebFlux trên JDK 9+. Binder có khả năng ánh xạ request parameters vào nested object properties.

Trong các deployment đặc thù, attacker có thể điều khiển property path đi sâu vào object graph / class-related properties thay vì chỉ business DTO fields.

Exploit phổ biến yêu cầu:

- JDK 9+;
- ứng dụng Spring MVC;
- deploy WAR trên Apache Tomcat;
- endpoint có data binding phù hợp.

Một attack chain điển hình lợi dụng property binding để thay đổi Tomcat logging/access-log configuration, khiến server ghi nội dung attacker kiểm soát thành file web-accessible có khả năng thực thi như JSP.

```text
HTTP parameters
    ↓
Spring data binder
    ↓
unexpected class/container properties
    ↓
Tomcat configuration manipulation
    ↓
write executable server-side content
    ↓
RCE
```

Root cause: binding surface quá rộng và thiếu restrictions đối với dangerous property paths.

### Severity

- **CVSS v3.1: 9.8 — Critical**

### Consequences

Attacker từ xa có thể:

- thực thi code với quyền application server;
- đọc/sửa dữ liệu;
- cài web shell;
- lấy credential;
- pivot sang hệ thống nội bộ.

### Solution

Spring phát hành bản vá:

- Spring Framework 5.3.18+
- 5.2.20+

Các defensive measures:

- upgrade framework;
- tránh deploy WAR nếu không cần;
- restrict allowed data-binding fields;
- không bind request trực tiếp vào objects có surface lớn;
- dùng explicit DTOs;
- chạy server với least privilege.

---

## 7. Microsoft Follina / MSDT – CVE-2022-30190

### Defect name

**Microsoft Support Diagnostic Tool (MSDT) Remote Code Execution — CVE-2022-30190 (“Follina”)**

### Source links

- Microsoft MSRC: https://www.microsoft.com/en-us/msrc/blog/2022/05/guidance-for-cve-2022-30190-microsoft-support-diagnostic-tool-vulnerability
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2022-30190

### Description

Follina lợi dụng việc ứng dụng như Microsoft Word có thể gọi **`ms-msdt:` URL protocol handler**.

Một crafted Office document có thể tham chiếu external content. Nội dung này cuối cùng kích hoạt MSDT thông qua protocol URI với parameters do attacker kiểm soát.

Conceptual flow:

```text
malicious document
     ↓
Office loads remote HTML/content
     ↓
ms-msdt: protocol
     ↓
MSDT parameter processing
     ↓
command/script execution
```

Điểm đáng chú ý là attack không phụ thuộc vào VBA macro truyền thống. Vì vậy các security assumptions kiểu “disable macros là đủ” không chặn được vector này.

Root cause là unsafe composition giữa:

- document renderer;
- custom URL protocol;
- diagnostic executable;
- attacker-controlled arguments.

### Severity

Microsoft/NVD xếp lỗ hổng ở mức **High — CVSS v3.1: 7.8**.

### Consequences

Code chạy với quyền của ứng dụng gọi MSDT / user hiện tại:

- install program;
- đọc/thay đổi/xóa dữ liệu;
- tạo account;
- chạy PowerShell hoặc payload tiếp theo.

### Solution

Microsoft phát hành Windows updates vào tháng 6/2022 và defense-in-depth updates sau đó.

Temporary workaround thời điểm đầu:

- disable `ms-msdt` URL protocol handler.

Long-term:

- install security updates;
- hạn chế protocol-handler attack surface;
- EDR detect Office spawning diagnostic/script tooling;
- least privilege cho endpoint users.

---

## 8. Microsoft Outlook NTLM credential leak – CVE-2023-23397

### Defect name

**Microsoft Outlook Elevation of Privilege / Net-NTLMv2 Credential Leak — CVE-2023-23397**

### Source links

- Microsoft technical guidance: https://www.microsoft.com/en-us/security/blog/2023/03/24/guidance-for-investigating-attacks-using-cve-2023-23397/
- MSRC: https://www.microsoft.com/msrc/blog/2023/03/microsoft-mitigates-outlook-elevation-of-privilege-vulnerability
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2023-23397

### Description

Attacker gửi email chứa extended MAPI property **`PidLidReminderFileParameter`** trỏ tới UNC path trên SMB server do attacker kiểm soát.

Ví dụ logic:

```text
crafted Outlook message
      ↓
PidLidReminderFileParameter =
\\attacker-server\share\file
      ↓
Outlook reminder processing
      ↓
automatic SMB connection
      ↓
NTLM authentication negotiation
      ↓
Net-NTLMv2 material sent to attacker
```

Điểm nghiêm trọng: exploit có thể trigger khi Outlook xử lý reminder, **không cần user mở attachment hoặc click link**.

Attacker sau đó có thể:

- relay NTLM authentication sang service khác;
- hoặc crack hash offline tùy credential strength.

Root cause là application tự động dereference untrusted remote UNC resource trong privileged authentication context.

### Severity

**Critical — CVSS v3.1: 9.8** (Microsoft và NVD).

### Consequences

- credential material leakage;
- NTLM relay;
- lateral movement;
- privilege escalation trong domain;
- compromise account và internal services.

### Solution

Microsoft patch thay đổi behavior để Outlook không honor remote untrusted path như trước.

Defense-in-depth:

- block outbound SMB TCP/445 ra Internet;
- disable NTLM khi có thể;
- enable SMB signing / Extended Protection phù hợp;
- monitor suspicious UNC paths;
- patch cả Outlook client, không chỉ mail server.

---

## 9. MOVEit Transfer SQL Injection – CVE-2023-34362

### Defect name

**Progress MOVEit Transfer SQL Injection — CVE-2023-34362**

### Source links

- NVD: https://nvd.nist.gov/vuln/detail/CVE-2023-34362
- Progress FAQ/advisory: https://www.progress.com/docs/default-source/moveit-docs/moveit-transfer_moveit-cloud-vulnerabilities-customer-faq_posted.pdf

### Description

MOVEit Transfer có SQL injection trong web application cho phép unauthenticated attacker truy cập database.

Root flow:

```text
HTTP/HTTPS request
      ↓
insufficient SQL input handling
      ↓
attacker-controlled SQL fragments
      ↓
MOVEit database
```

Tùy DB engine (MySQL, SQL Server, Azure SQL), attacker có thể:

- infer schema/data;
- đọc dữ liệu;
- thay đổi/xóa database objects;
- trong observed exploitation, dùng access để triển khai web shell/persistence và exfiltrate data.

Đây là classic failure của việc concatenate hoặc đưa untrusted values vào SQL context mà không parameterize/validate đúng cách.

### Severity

**Critical — CVSS v3.1: 9.8** (NVD) và được CISA đưa vào Known Exploited Vulnerabilities catalog.

### Consequences

Sự cố thực tế gây mass data theft tại nhiều tổ chức sử dụng MOVEit.

Technical impact:

- unauthorized DB access;
- file-transfer data disclosure;
- modification/deletion;
- account/session compromise;
- persistent web shell;
- supply-chain-like downstream exposure vì MOVEit thường chứa dữ liệu trao đổi với đối tác.

### Solution

Progress phát hành patches cho các supported branches và patch MOVEit Cloud.

Biện pháp:

- patch ngay;
- kiểm tra IoCs/web shells;
- rotate credentials;
- review DB/file access logs;
- isolate internet-exposed MFT;
- parameterized queries và least-privilege DB account.

---

## 10. Cisco IOS XE Web UI privilege escalation – CVE-2023-20198

### Defect name

**Cisco IOS XE Web UI Privilege Escalation — CVE-2023-20198**

### Source links

- Cisco advisory: https://www.cisco.com/c/en/us/support/docs/csa/cisco-sa-iosxe-webui-privesc-j22SaA4z.html
- Cisco TAC FAQ: https://www.cisco.com/c/en/us/support/docs/ios-nx-os-software/ios-xe-17/221144-cisco-tac-technical-faqs-for-cisco-ios-x.html

### Description

Lỗ hổng ảnh hưởng IOS XE khi Web UI HTTP/HTTPS server được bật.

Cisco xác định attacker đã chain hai zero-days:

1. **CVE-2023-20198** để có initial access và tạo local user privilege 15;
2. **CVE-2023-20273** sau đó được dùng để nâng tiếp tới root và ghi implant vào filesystem.

Simplified chain:

```text
Internet-exposed Web UI
       ↓
CVE-2023-20198
       ↓
unauthorized privilege-15 account
       ↓
authenticated Web UI access
       ↓
CVE-2023-20273
       ↓
root-level command execution / implant
```

Root cause của CVE-2023-20198 thuộc nhóm broken access control / insufficient authorization ở Web UI.

### Severity

- **CVSS 10.0 — Critical**

### Consequences

- tạo admin-level account trái phép;
- thay đổi router/switch configuration;
- credential collection;
- network traffic interception;
- root implant;
- persistence;
- compromise thiết bị hạ tầng mạng.

### Solution

- upgrade tới fixed IOS XE releases;
- nếu không cần Web UI, disable `ip http server` và `ip http secure-server`;
- hạn chế management plane bằng ACL/VPN;
- kiểm tra local accounts và IoCs;
- reimage/rebuild thiết bị đã compromise khi cần.

---

## 11. libwebp heap buffer overflow – CVE-2023-4863

### Defect name

**libwebp Heap Buffer Overflow / Out-of-Bounds Write — CVE-2023-4863**

### Source links

- NVD: https://nvd.nist.gov/vuln/detail/CVE-2023-4863
- Chrome releases: https://chromereleases.googleblog.com/

### Description

Lỗi nằm trong xử lý ảnh WebP của `libwebp`. Crafted WebP có thể khiến decoder thực hiện **out-of-bounds write** trên heap.

Conceptual memory-safety failure:

```text
crafted compressed image
       ↓
decoder calculates/uses invalid bounds
       ↓
write beyond allocated heap buffer
       ↓
memory corruption
```

Vì libwebp được nhúng trong nhiều browser/application, defect trong một image library có blast radius rất lớn.

Trong exploitation context của browser:

```text
victim loads malicious page/image
       ↓
WebP decoder
       ↓
heap corruption
       ↓
potential code execution in renderer process
```

Root cause: thiếu memory-safe boundary enforcement trong native C/C++ image decoding.

### Severity

- **CVSS v3.1: 8.8 — High**
- Chromium xếp security severity: **Critical**

### Consequences

- crash;
- memory corruption;
- arbitrary code execution tùy exploit chain;
- browser compromise;
- ảnh hưởng nhiều sản phẩm dùng chung libwebp.

### Solution

- upgrade `libwebp` lên 1.3.2+;
- update Chrome/Edge/Firefox/Thunderbird và ứng dụng đóng gói vulnerable library;
- inventory transitive dependencies;
- fuzz image decoders;
- dùng memory-safe implementation khi khả thi;
- compiler hardening, ASLR, sandbox để giảm exploitability.

---

## 12. GitLab password-reset account takeover – CVE-2023-7028

### Defect name

**GitLab Password Reset to Unverified Email → Account Takeover — CVE-2023-7028**

### Source links

- GitLab security release: https://docs.gitlab.com/releases/patches/patch-release-gitlab-16-7-2-released/
- GitLab CVE record: https://gitlab.com/gitlab-org/cves/-/blob/5dbfc725a86e6d942deec9c36b7f06f5b8d912fc/2023/CVE-2023-7028.json
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2023-7028

### Description

Password reset logic có thể gửi reset email tới **unverified email address**.

Security invariant đúng phải là:

```text
password reset destination
        ∈
verified addresses owned by account
```

Nhưng vulnerable flow cho phép request manipulation dẫn tới:

```text
victim account
     ↓
password reset request
     ↓
attacker-controlled unverified address
     ↓
reset token delivered to attacker
```

Đây là **business-logic / identity recovery defect**, không cần memory corruption hay injection.

Root cause: trust không đúng vào recovery-address input và thiếu verification invariant trước khi phát reset token.

### Severity

- **CVSS v3.1: 10.0 — Critical** (GitLab, đơn vị cấp CVE)
- NVD (Primary): **CVSS v3.1: 9.8 — Critical**

### Consequences

Attacker không cần victim interaction để có thể takeover account.

Nếu victim là maintainer/admin:

- source-code theft;
- malicious commits;
- CI/CD secret theft;
- pipeline modification;
- software supply-chain compromise.

### Solution

GitLab phát hành fixed versions:

- 16.7.2
- 16.6.4
- 16.5.6
- 16.4.5
- 16.3.7
- 16.2.9
- 16.1.6

Khuyến nghị:

- update lên bản mới hơn;
- kiểm tra password-reset/audit events;
- reset credentials nếu nghi ngờ;
- enforce 2FA;
- với recovery workflow, chỉ gửi token tới verified ownership channels.

---

## 13. Atlassian Confluence Broken Access Control – CVE-2023-22515

### Defect name

**Confluence Data Center/Server Broken Access Control / Privilege Escalation — CVE-2023-22515**

### Source links

- Atlassian advisory: https://confluence.atlassian.com/security/cve-2023-22515-privilege-escalation-vulnerability-in-confluence-data-center-and-server-1295682276.html
- Atlassian FAQ: https://support.atlassian.com/atlassian-knowledge-base/kb/faq-for-cve-2023-22515/
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2023-22515

### Description

Publicly accessible Confluence Server/Data Center 8.x có broken access control cho phép external attacker tạo unauthorized Confluence administrator accounts.

Security state machine đáng lẽ:

```text
initial setup complete
       ↓
setup/admin endpoints permanently restricted
```

Vulnerability làm một số setup-related actions vẫn có thể bị truy cập/manipulate theo cách khiến instance quay lại hoặc đi vào privileged setup flow.

Kết quả:

```text
unauthenticated request
      ↓
access-control/state validation failure
      ↓
administrator creation
      ↓
full Confluence access
```

### Severity

- **CVSS 10.0 — Critical** (Atlassian, CVSS v3.0)
- NVD (Primary): **CVSS v3.1: 9.8 — Critical**

### Consequences

- attacker tạo admin account;
- đọc toàn bộ spaces/pages;
- lấy credentials/secrets lưu trong wiki;
- cài plugin hoặc abuse admin functionality;
- pivot sang internal systems;
- data exfiltration.

Atlassian cũng ghi nhận active exploitation.

### Solution

Fixed versions gồm:

- 8.3.3+
- 8.4.3+
- 8.5.2+

Nếu chưa patch được:

- cô lập khỏi Internet;
- restrict access;
- threat hunt unauthorized admins;
- kiểm tra filesystem/process/logs;
- assume compromise nếu Internet-exposed vulnerable instance có suspicious artifacts.

---

## 14. glibc Looney Tunables – CVE-2023-4911

### Defect name

**GNU glibc `GLIBC_TUNABLES` Buffer Overflow (“Looney Tunables”) — CVE-2023-4911**

### Source links

- NVD: https://nvd.nist.gov/vuln/detail/CVE-2023-4911
- Qualys technical analysis: https://blog.qualys.com/vulnerabilities-threat-research/2023/10/03/cve-2023-4911-looney-tunables-local-privilege-escalation-in-the-glibcs-ld-so

### Description

Lỗ hổng nằm trong dynamic loader `ld.so` khi parse environment variable `GLIBC_TUNABLES`.

Một crafted environment string có thể gây buffer overflow trong quá trình xử lý tunables.

Attack chain:

```text
local attacker
     ↓
crafted GLIBC_TUNABLES
     ↓
launch SUID binary
     ↓
ld.so parses environment
     ↓
buffer overflow
     ↓
control process running with elevated privilege
```

Điểm quan trọng là dynamic loader chạy **trước application main()** và trong SUID context có thể chạy với quyền cao hơn user.

Root cause:

- unsafe memory manipulation;
- parsing/length accounting không đúng;
- privileged code path xử lý attacker-influenced environment data.

### Severity

- **CVSS v3.1: 7.8 — High**

### Consequences

Local user có thể escalate tới root trên các Linux distributions bị ảnh hưởng.

Hậu quả:

- full host takeover;
- disable security controls;
- credential theft;
- install persistence/rootkit;
- lateral movement.

### Solution

- update glibc package từ distro vendor;
- reboot/restart affected services nếu cần để dùng patched libraries;
- hạn chế local shell access;
- harden SUID surface;
- fuzz environment/config parsers trong privileged components.

---

## 15. XZ Utils supply-chain backdoor – CVE-2024-3094

### Defect name

**XZ Utils / liblzma Supply-Chain Backdoor — CVE-2024-3094**

### Source links

- NVD: https://nvd.nist.gov/vuln/detail/CVE-2024-3094
- Red Hat tracking: https://bugzilla.redhat.com/show_bug.cgi?id=2272210
- Red Hat retrospective: https://www.redhat.com/en/blog/2024-red-hat-product-security-risk-report-cves-xz-backdoor-sscas-aioh-my

### Description

Đây không phải accidental coding bug mà là **malicious supply-chain defect**.

Upstream tarballs của XZ 5.6.0 và 5.6.1 chứa build-time logic bị obfuscate. Trong quá trình build, script:

1. lấy dữ liệu từ file test được ngụy trang;
2. extract prebuilt malicious object;
3. chèn object vào `liblzma`;
4. library đã bị sửa có thể can thiệp vào interaction của phần mềm link với nó.

Simplified:

```text
apparently legitimate source tarball
       ↓
obfuscated build logic
       ↓
extract hidden binary object
       ↓
modify liblzma at build time
       ↓
downstream software loads compromised library
```

Điểm tinh vi là malicious logic tập trung ở **release tarball/build pipeline**, làm source-review thông thường khó nhận ra.

Trong một số Linux integration paths, compromised `liblzma` có thể ảnh hưởng tới `sshd` thông qua dependency chain.

### Severity

- **CVSS v3.1: 10.0 — Critical**
- CWE-506: Embedded Malicious Code.

### Consequences

Nếu backdoor lan rộng vào production distributions:

- remote authentication bypass / unauthorized SSH access;
- compromise servers;
- supply-chain compromise ở quy mô lớn;
- integrity failure của open-source build/release process.

### Solution

- remove/downgrade XZ 5.6.0/5.6.1;
- dùng known-good versions/distribution packages;
- verify package provenance;
- reproducible builds;
- compare release tarball với repository source;
- signed artifacts;
- multi-maintainer review cho critical release pipeline;
- SBOM/provenance/SLSA-style controls.

---

## 16. Palo Alto PAN-OS GlobalProtect command injection – CVE-2024-3400

### Defect name

**PAN-OS GlobalProtect Arbitrary File Creation → OS Command Injection — CVE-2024-3400**

### Source links

- Palo Alto advisory: https://security.paloaltonetworks.com/CVE-2024-3400
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2024-3400

### Description

Palo Alto mô tả đây là command injection xuất phát từ **arbitrary file creation** trong GlobalProtect.

Affected firewall có GlobalProtect gateway/portal enabled có thể bị unauthenticated attacker khai thác qua network.

Conceptual chain:

```text
unauthenticated request
       ↓
insufficient validation
       ↓
attacker-controlled file/path/content creation
       ↓
file later consumed by privileged processing
       ↓
OS command injection
       ↓
root code execution
```

Đây là ví dụ của **second-order injection**: request ban đầu tạo artifact, sau đó một privileged component đọc/xử lý artifact và biến dữ liệu thành command context.

### Severity

- **CVSS 10.0 — Critical**

Attack requirements:

- network accessible;
- no privileges;
- no user interaction;
- root-level impact.

### Consequences

- arbitrary code as root trên firewall;
- steal config/credentials;
- traffic interception;
- persistence;
- disable network protections;
- pivot vào internal network.

Palo Alto xác nhận exploitation in the wild.

### Solution

- upgrade ngay tới fixed PAN-OS releases;
- apply Threat Prevention signatures/mitigation nếu patch chưa thể triển khai;
- hunt compromise indicators;
- với exploited device, thực hiện recovery theo vendor guidance;
- giới hạn management/services exposure.

---

## 17. Check Point Security Gateway information disclosure – CVE-2024-24919

### Defect name

**Check Point Security Gateway / VPN Information Disclosure — CVE-2024-24919**

### Source links

- Check Point advisory: https://advisories.checkpoint.com/defense/advisories/public/2024/cpai-2024-0353.html/
- Check Point security notice: https://blog.checkpoint.com/security/enhance-your-vpn-security-posture
- Technical reverse engineering: https://labs.watchtowr.com/check-point-wrong-check-point-cve-2024-24919/

### Description

Vulnerability ảnh hưởng một số Internet-connected Security Gateways có Remote Access VPN hoặc Mobile Access.

Technical analysis cho thấy endpoint liên quan `/clients/MyCRL` phục vụ filesystem content. Input trong request body có thể đi qua file-path handling không đủ chặt, tạo khả năng đọc file ngoài intended directory.

Conceptual path:

```text
unauthenticated HTTP request
        ↓
/clients/MyCRL handler
        ↓
insufficient path sanitization
        ↓
filesystem traversal / arbitrary file access
        ↓
sensitive file disclosure
```

Đây là failure ở trust boundary giữa HTTP request và filesystem path.

### Severity

Vendor và NVD xếp **High — CVSS v3.1: 8.6**.

### Consequences

Sensitive information có thể bị đọc từ Security Gateway.

Tùy file bị lấy:

- credential/hash disclosure;
- VPN/account compromise;
- attacker dùng thông tin để vào remote-access environment;
- lateral movement.

### Solution

Check Point phát hành hotfix/fix và yêu cầu khách hàng cài đặt.

Ngoài patch:

- update IPS protection;
- đổi các password-only local VPN accounts;
- dùng MFA;
- review VPN/auth logs;
- kiểm tra indicators of compromise;
- tránh expose management endpoints không cần thiết.

---

## 18. PHP-CGI Windows argument injection – CVE-2024-4577

### Defect name

**PHP-CGI Argument Injection on Windows “Best-Fit” Code Pages — CVE-2024-4577**

### Source links

- NVD: https://nvd.nist.gov/vuln/detail/CVE-2024-4577
- PHP security releases: https://www.php.net/releases/

### Description

Khi PHP chạy ở CGI mode trên Windows và system dùng một số code pages, Windows **Best-Fit character conversion** có thể biến một Unicode/encoded character thành ASCII character có ý nghĩa đặc biệt đối với command-line parser.

Kết quả: attacker-controlled URL/query data sau Unicode/code-page conversion có thể được PHP CGI hiểu thành command-line options.

```text
HTTP input
   ↓
Windows code-page conversion
   ↓
Best-Fit maps character
   ↓
unexpected "-" / option syntax
   ↓
php-cgi interprets attacker data as arguments
   ↓
PHP configuration override / code execution
```

Đây là lỗi **canonicalization mismatch**: validation nhìn một representation, nhưng downstream parser nhìn representation sau conversion khác.

### Severity

- **CVSS v3.1: 9.8 — Critical**

### Consequences

Attacker có thể:

- expose PHP script source;
- thay đổi PHP runtime flags;
- chạy arbitrary PHP code;
- đạt remote server compromise.

### Solution

Upgrade:

- 8.1.29+
- 8.2.20+
- 8.3.8+

Bổ sung:

- tránh CGI deployment trên Windows nếu không cần;
- WAF/routing restrictions;
- kiểm soát encoding/canonicalization;
- validate **sau** normalization theo đúng representation mà downstream interpreter sẽ thấy.

---

## 19. OpenSSH regreSSHion – CVE-2024-6387

### Defect name

**OpenSSH `sshd` Signal Handler Race Condition (“regreSSHion”) — CVE-2024-6387**

### Source links

- NVD: https://nvd.nist.gov/vuln/detail/CVE-2024-6387
- Qualys research: https://www.qualys.com/regresshion-cve-2024-6387/

### Description

Đây là security regression của issue cũ CVE-2006-5051.

`sshd` có signal-handling path chạy khi authentication vượt quá `LoginGraceTime`. Signal handler gọi logic không **async-signal-safe**.

Race condition:

```text
remote connection
     ↓
authentication intentionally delayed
     ↓
SIGALRM / timeout fires
     ↓
signal handler interrupts process
     ↓
unsafe functions manipulate shared heap/state
     ↓
memory corruption under precise race timing
```

Vấn đề cốt lõi: signal handler có thể chạy giữa lúc allocator/global state đang ở trạng thái không nhất quán. Nếu handler gọi hàm như logging/allocation không signal-safe, heap state có thể bị corrupt.

### Severity

- **CVSS v3.1: 8.1 — High**

Attack complexity được xếp High vì exploit cần thắng race condition nhiều lần.

### Consequences

Trên một số glibc-based Linux systems, unauthenticated remote attacker có thể đạt code execution trong pre-auth `sshd` context, thường có privilege rất cao.

Hậu quả:

- remote host takeover;
- credential theft;
- persistence;
- lateral movement.

### Solution

- update OpenSSH tới patched vendor version;
- distro security updates;
- giảm attack surface của SSH;
- rate limit connections;
- restrict source networks khi có thể;
- trong emergency, vendor-specific mitigation cho LoginGraceTime có thể giảm vector nhưng có trade-off DoS/resource exhaustion.

---

## 20. CrowdStrike Falcon Channel File 291 outage

### Defect name

**CrowdStrike Falcon Windows Sensor — Channel File 291 Content Update Validation Defect**

### Source links

- CrowdStrike Preliminary Post Incident Review: https://www.crowdstrike.com/en-us/blog/falcon-content-update-preliminary-post-incident-report/
- Technical details: https://www.crowdstrike.com/en-us/blog/falcon-update-for-windows-hosts-technical-details/
- RCA announcement: https://www.crowdstrike.com/en-us/blog/channel-file-291-rca-available/
- Technical OOB explanation: https://www.crowdstrike.com/en-us/blog/tech-analysis-addressing-claims-about-falcon-sensor-vulnerability/

### Description

Ngày 19/07/2024, CrowdStrike phát hành Rapid Response Content update cho Windows Falcon sensor. Một Template Instance chứa problematic content data vẫn vượt qua validation do **bug trong Content Validator**.

CrowdStrike sau đó xác định incident gây **out-of-bounds memory read** trong Windows kernel context, dẫn tới crash/BSOD.

Failure chain:

```text
Rapid Response Content
       ↓
Content Validator
       ↓
validator bug fails to reject invalid content
       ↓
content distributed globally
       ↓
Falcon sensor consumes malformed configuration
       ↓
out-of-bounds memory read
       ↓
kernel crash / BSOD
```

Điểm software-engineering quan trọng là deployment path cho fast-response content không có cùng mức staged rollout/blast-radius control như một traditional sensor release.

Đây không phải cyberattack; CrowdStrike xác nhận đó là lỗi content update.

### Severity

Không có CVE/CVSS cho bản chất incident này.

**Đánh giá operational impact: Critical**

Lý do: defect nằm trong kernel-level endpoint security software và được phân phối rộng, gây outage trên quy mô lớn.

### Consequences

- Windows hosts crash/boot-loop;
- endpoint không usable;
- disruption tới airlines, healthcare, banks, enterprises và các service phụ thuộc Windows;
- recovery phức tạp do một số máy cần thao tác thủ công/boot recovery;
- secondary risk: attackers lợi dụng incident để phishing/phát tán fake hotfix.

### Solution

Immediate:

- CrowdStrike revert problematic content lúc 05:27 UTC;
- recovery affected Windows hosts;
- sử dụng official remediation instructions.

Process/architecture improvements CrowdStrike công bố:

- tăng test coverage cho Rapid Response Content;
- bổ sung validation checks;
- cải thiện Content Validator;
- staged/ring deployment;
- tăng observability;
- cho khách hàng khả năng kiểm soát rollout content tốt hơn;
- kiểm thử failure modes của Template Instances trước global deployment.

Bài học kiến trúc:

```text
fast update
   ≠
skip safety gates
```

Critical kernel/security content cần:

```text
schema validation
   +
semantic validation
   +
canary
   +
progressive rollout
   +
automatic rollback
   +
blast-radius controls
```

---

# Phần C — Chỗ AI thiên lệch / hallucinate khi giải thích lỗi

**Công cụ:** ChatGPT (bản web, có web search). Prompt và timestamp: xem [ai/prompt_log.md](../ai/prompt_log.md).
**Case bị ảnh hưởng:** #4 — Air Canada Bereavement Chatbot.

## Nội dung AI viết trong câu trả lời gốc

ChatGPT gắn nhãn hallucination cho case này ở ba chỗ:

- Tiêu đề: "4. Air Canada Chatbot — **Hallucinated** Bereavement Fare Policy".
- Bảng tóm tắt: Type = "**Hallucination** / incorrect policy generation".
- Mục chi tiết: "**Type:** Hallucination / incorrect generated information."

Nhưng cũng trong câu trả lời đó, mục "Important technical limitation" lại viết:

> "the public case record did **not disclose the chatbot's technical architecture or model**. ... it would be technically incorrect to claim with certainty that it used: GPT, RAG, transformer architecture, a specific LLM."

## Vì sao đây là thiên lệch

1. **Tự mâu thuẫn:** nhãn ở tiêu đề, bảng và mục Type khẳng định "hallucination", còn phần thân thừa nhận hồ sơ vụ án không cho biết chatbot dùng công nghệ gì. Hallucination là thuật ngữ về hành vi của mô hình sinh (LLM), nên chưa thể gắn nhãn khi chưa biết chatbot có phải LLM hay không.
2. **Khả năng nguyên nhân (suy luận của sinh viên):** prompt yêu cầu ba nhóm lỗi (hallucination, prompt injection, bias). AI cần một case cho nhóm hallucination nên chọn vụ nổi tiếng có vẻ khớp và gắn nhãn theo khung của người hỏi. Đây là xu hướng chiều theo câu hỏi (prompt conformity / sycophancy) và gắn nhãn quá mức.
3. **Giả định trình bày như kết luận:** mục "Technical root cause" và "Solution" (thiếu grounding, dùng RAG, fact-consistency checker) suy ra một kiến trúc sinh văn bản mà hồ sơ không xác nhận.

Đây là thiên lệch dạng gắn nhãn quá mức và suy diễn kiến trúc, không phải bịa ra sự kiện: vụ Moffatt v. Air Canada có thật, chatbot đã đưa thông tin sai về chính sách vé tang lễ.

## Cách phát hiện

Đọc chéo phần thân với tiêu đề/bảng tóm tắt, sau đó đối chiếu với bản án: bản án không nêu công nghệ của chatbot.

## Cách sửa trong tài liệu này

- Đổi nhãn thành "incorrect generated response / hallucination-like failure" (bảng tổng hợp và case 4).
- Giữ "Lưu ý kỹ thuật quan trọng" ở case 4 và chỉ mô tả lỗi ở mức thiết kế hệ thống (câu trả lời không khớp nguồn chính sách chính thức), không khẳng định mô hình cụ thể.
- Dẫn trực tiếp bản án thay vì blog.

## Bài học khi làm việc với AI

Khi bắt AI điền vào một phân loại có sẵn, cần kiểm tra từng mục xem có bằng chứng thật cho nhãn hay không, và yêu cầu AI tách rõ "sự kiện có nguồn" với "suy luận".

## Quan sát bổ sung (case 3 — EmailGPT)

Câu trả lời gốc chỉ nêu điểm của đơn vị cấp CVE (v4 8.5 / v3.1 6.5) và giải thích chênh lệch bằng "khác phiên bản CVSS". Tra NVD API cho thấy NVD chấm riêng **9.1 Critical**, nên chênh lệch còn do khác đơn vị chấm điểm. Câu trả lời bỏ sót nguồn NVD.

---

# So sánh theo nguyên nhân gốc (Root Cause Taxonomy)

| Root cause                                   | Cases                                                    |
| -------------------------------------------- | -------------------------------------------------------- |
| Untrusted input reaches code execution       | LangChain, Vanna, Spring4Shell, Follina, PHP-CGI, PAN-OS |
| Improper access control / identity logic     | GitLab, Confluence, Cisco IOS XE                         |
| Injection into interpreter/query             | MOVEit SQLi, PAN-OS command injection                    |
| Memory safety                                | libwebp, glibc, OpenSSH                                  |
| Unsafe protocol/resource dereference         | Outlook NTLM leak, Follina                               |
| Model/output not grounded in source of truth | Air Canada                                               |
| Model objective / fairness mismatch          | Meta Housing Ads                                         |
| Supply-chain integrity failure               | XZ Utils                                                 |
| Validation + rollout failure                 | CrowdStrike                                              |
| Filesystem/path validation                   | Check Point                                              |
| Prompt as security boundary                  | EmailGPT                                                 |
| LLM output trusted as executable code        | LangChain, Vanna                                         |

---

# Các mẫu lỗi kiến trúc rút ra

## 1. Untrusted input không chỉ là user text

Trong hệ thống hiện đại, các nguồn sau đều phải được xem là untrusted:

```text
HTTP input
email metadata
document content
image file
environment variable
LLM output
generated SQL
model-generated code
configuration update
third-party package
```

Một component tạo ra dữ liệu không có nghĩa dữ liệu đó đáng tin đối với component kế tiếp.

## 2. Validate tại đúng trust boundary

Sai:

```text
validate representation A
      ↓
decode / normalize / convert
      ↓
interpreter consumes representation B
```

Đúng:

```text
decode / canonicalize
      ↓
validate exact representation
      ↓
typed parser / allowlist
      ↓
execution
```

PHP-CGI là ví dụ điển hình của lỗi canonicalization mismatch.

## 3. Không dùng probabilistic component làm security boundary

```text
user
 ↓
LLM: "please don't do dangerous things"
 ↓
tool / exec
```

không phải kiến trúc an toàn.

Security enforcement cần nằm ở deterministic layer:

```text
LLM output
   ↓
policy engine
   ↓
authorization
   ↓
schema validator
   ↓
restricted action
```

## 4. Recovery/authentication flow là security-critical business logic

GitLab CVE-2023-7028 cho thấy không cần buffer overflow hay RCE để có Critical vulnerability.

Một sai invariant:

```text
reset token → wrong email
```

cũng có thể dẫn đến full account takeover.

## 5. Shared libraries làm tăng blast radius

libwebp, glibc và XZ cho thấy defect ở dependency cấp thấp có thể xuất hiện trong hàng nghìn downstream products.

Cần:

- SBOM;
- dependency inventory;
- automated vulnerability scanning;
- provenance;
- reproducible builds;
- emergency patch pipeline.

## 6. Progressive delivery là một safety mechanism

CrowdStrike cho thấy testing trước release chưa đủ.

Cần:

```text
test
 ↓
canary
 ↓
small ring
 ↓
monitor
 ↓
gradual rollout
 ↓
automatic rollback
```

đặc biệt với kernel agents, endpoint security software, firmware và global configuration.

---

# Kết luận

20 case trên cho thấy “software defect” không chỉ là bug cú pháp hoặc logic đơn giản. Các defect nghiêm trọng thường xuất hiện tại **ranh giới giữa các component**:

```text
user input ↔ parser
model output ↔ interpreter
web request ↔ filesystem
application ↔ operating system
identity workflow ↔ authorization
ML objective ↔ business/legal requirement
build system ↔ package artifact
update service ↔ production fleet
```

Một principle có thể áp dụng cho cả traditional software và AI software là:

```text
Never trust data merely because it came from another component.
```

Trong AI systems, principle này mở rộng thành:

```text
LLM output is untrusted input.
```

Và trong production deployment:

```text
A validated update is still not equivalent to a safe global rollout.
```

Do đó một defensive architecture tốt cần kết hợp:

- explicit trust boundaries;
- input normalization + validation;
- allowlists và typed schemas;
- least privilege;
- sandbox;
- deterministic authorization;
- memory-safe implementation khi khả thi;
- dependency provenance;
- observability;
- canary/progressive rollout;
- automatic rollback;
- threat modeling và negative/adversarial testing.

---

# Tài liệu tham khảo chính

1. LangChain / CVE-2023-29374 — https://github.com/advisories/GHSA-fprp-p869-w6q2
2. Vanna.AI / CVE-2024-5565 — https://jfrog.com/blog/prompt-injection-attack-code-execution-in-vanna-ai-cve-2024-5565/
3. EmailGPT / CVE-2024-5184 — https://www.cve.org/CVERecord?id=CVE-2024-5184
4. Air Canada / Moffatt — https://www.canlii.org/en/bc/bccrt/doc/2024/2024bccrt149/2024bccrt149.html
5. Meta housing ads — https://www.justice.gov/crt/case/united-states-v-meta-platforms-inc-fka-facebook-inc-sdny
6. Spring4Shell — https://nvd.nist.gov/vuln/detail/CVE-2022-22965
7. Follina — https://www.microsoft.com/en-us/msrc/blog/2022/05/guidance-for-cve-2022-30190-microsoft-support-diagnostic-tool-vulnerability
8. Outlook CVE-2023-23397 — https://www.microsoft.com/en-us/security/blog/2023/03/24/guidance-for-investigating-attacks-using-cve-2023-23397/
9. MOVEit — https://nvd.nist.gov/vuln/detail/CVE-2023-34362
10. Cisco IOS XE — https://www.cisco.com/c/en/us/support/docs/csa/cisco-sa-iosxe-webui-privesc-j22SaA4z.html
11. libwebp — https://nvd.nist.gov/vuln/detail/CVE-2023-4863
12. GitLab — https://docs.gitlab.com/releases/patches/patch-release-gitlab-16-7-2-released/
13. Confluence — https://confluence.atlassian.com/security/cve-2023-22515-privilege-escalation-vulnerability-in-confluence-data-center-and-server-1295682276.html
14. glibc Looney Tunables — https://nvd.nist.gov/vuln/detail/CVE-2023-4911
15. XZ Utils — https://nvd.nist.gov/vuln/detail/CVE-2024-3094
16. PAN-OS — https://security.paloaltonetworks.com/CVE-2024-3400
17. Check Point — https://advisories.checkpoint.com/defense/advisories/public/2024/cpai-2024-0353.html/
18. PHP-CGI — https://nvd.nist.gov/vuln/detail/CVE-2024-4577
19. OpenSSH regreSSHion — https://nvd.nist.gov/vuln/detail/CVE-2024-6387
20. CrowdStrike Channel File 291 — https://www.crowdstrike.com/en-us/blog/falcon-content-update-preliminary-post-incident-report/
