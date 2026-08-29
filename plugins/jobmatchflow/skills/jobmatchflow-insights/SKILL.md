---
name: jobmatchflow-insights
description: Analyze a user's JobMatchFlow application funnel, stage timing, targeting patterns, and observed outcomes from existing App data. Use only when the user explicitly asks for outcome analysis, funnel analysis, or strategy calibration. Do not invoke during ordinary application or inbox workflows.
---

# JobMatchFlow Insights

This is a read-only analysis workflow. JobMatchFlow remains the source of truth; do not create another outcome database and do not modify profile, matching rules, or application history. Read JobMatchFlow only through its MCP tools; never operate the App frontend in a browser.

## Gather

1. Read current tracking and jobs from JobMatchFlow. Use existing stage, score, source, resume choice, dates, role family, sector, and location fields when present.
   When the user needs all Application information, use `list_tracking` to enumerate every record and then call `get_application_context` for each `tracking_id`; this is where the submitted CV and Cover Letter snapshot, full JD, score, dates, status, and unified notes are retrieved.
   Use `download_application_material` only when the user needs the actual submitted CV or Cover Letter files rather than their context, metadata, or text.
2. Read recruiter feedback from the unified application notes when available and include it as qualitative evidence. Missing feedback must not block quantitative analysis.
3. State the analysis date, included population, exclusions, and missing fields.

## Analyze

- Show total sample size and counts at each funnel stage.
- Calculate conversion and time-to-stage only when the underlying dates exist.
- Compare useful dimensions such as role family, sector, source/channel, match-score band, location, and resume choice.
- Suppress or clearly label comparisons based on very small groups.
- Treat patterns as correlations. Do not claim that one resume, keyword, or source caused an outcome without an actual experiment.
- Use feedback to explain plausible hypotheses, not to rewrite observed statuses.

## Deliver

Give a compact report with:

1. what the data reliably shows;
2. what remains uncertain;
3. targeting choices to continue or stop;
4. one or two bounded experiments for the next application pulse;
5. the metric and sample threshold for evaluating each experiment.

Do not automatically edit Basic Info, Experience, resumes, scoring, jobs, or tracking records.
