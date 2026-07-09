# AGENTS.md — PHYSICAL DESIGN (OpenROAD) ENTRYPOINT

> [!IMPORTANT]
> **MANDATORY BOOT PROTOCOL**:
> 1. Xưng hô: **"Cậu chủ"**.
> 2. Đọc **Expert Protocol Manifesto** (`@doc/guides/expertprotocolmanifesto`). Nếu file thiếu, dùng `KNOWNS.md` làm fallback và báo cáo lại.
> 3. Kích hoạt **CLI Algorithm** (`D:\Project\Plan\CLI_Algorithm.md`) khi lập lịch.
> 4. Chỉ đọc thêm `GEMINI.md`, `AGENTS.md`, `CLAUDE extra.md` khi task yêu cầu đúng agent mode hoặc tool family tương ứng.
> 5. **Runtime capability**: Codex uses confirmed Knowns MCP and CLI tools.
> 6. **Skill Invocation**: Trước mọi phản hồi hoặc hành động, kiểm tra skill liên quan và đọc/dùng skill đó; tối thiểu `using-superpowers` là rule nền cho mọi phiên.

## 🚀 CONTEXT ENGINE — LAZY-LOAD STRATEGY

AI **KHÔNG** đọc tất cả file cùng lúc. Tuân thủ quy trình:

```
[BOOT]   → Đọc ROOT AGENTS.md (file này) — BẮT BUỘC
   ↓
[DETECT] → Xác định domain từ working directory hoặc câu hỏi của Cậu chủ
   ↓
[LOAD]   → Đọc AGENTS.md của domain tương ứng (CHỈ 1 FILE)
   ↓
[ON-DEMAND] → Đọc reference docs khi task yêu cầu cụ thể
```

---

*Phục vụ Cậu chủ là ưu tiên cao nhất.*

<!-- KNOWNS GUIDELINES START -->

@d:\Project\KNOWNS.md

**CRITICAL: You MUST read and follow `KNOWNS.md` in the repository root before doing any work. It is the canonical source of truth for all agent behavior in this project.**

<!-- KNOWNS GUIDELINES END -->

## Tool/Skill Routing Addendum — 2026-07-09

- Before choosing a tool/skill, use `D:\Project\_tooling\tools\TOOL_SKILL_REGISTRY.md` as the canonical routing table.
- Active workflow source is Knowns MCP + local `kn-*` skills. Third-party agent repos under `D:\Project\_tooling\tools\ECC` and `D:\Project\_tooling\tools\agent-patterns` are reference-only unless a specific subfolder/file is scanned and approved.
- If skills overlap, route by source of truth: Knowns tasks/specs use `kn-*`; general coding discipline uses `karpathy-guidelines`, `systematic-debugging`, `test-driven-development`, and `verification-before-completion`.

## Folder-Specific Tool Routes — OpenROAD-RTL-to-GDS-Mini-Labs

- Domain: Physical design flows, Sky130 PDK, logic synthesis (Yosys), static timing analysis (OpenSTA), floorplanning, placement, routing, and DRC/LVS checks.
- First skill after baseline: `dv-assistant` / `career-ops`; use `drawio-local.ps1` for clock tree routing, cell density, placement blocks, and timing path diagrams.
- Use WSL `sta` for Static Timing Analysis validation.
- Use Yosys (`yosys.exe` in tools or WSL `yosys`) for RTL logic synthesis checks.
- Keep PnR claims strictly grounded in output logs and report summaries. Never claim PrimeTime, Innovus, or commercial PDK experience unless explicit logs are archived.
