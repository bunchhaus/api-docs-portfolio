# Documenting the DarwiNN SDK (Google, Internal)

## Overview

At Google, I was responsible for creating developer-facing documentation for an internal SDK that enabled machine learning (ML) researchers and engineers to run TensorFlow models efficiently on specialized hardware. The SDK, known internally as DarwiNN, provided a complete toolchain for model training, conversion, profiling, and deployment.

My role was to make this complex, hardware-integrated workflow clear, navigable, and productive for diverse developer audiences.

## The Challenge

- Complex Toolchain – The SDK spanned compilers, profilers, simulators, runtimes, and numerics validation.
- Diverse Users – From novice TensorFlow users who wanted “drop-in” simplicity, to advanced engineers seeking low-level TPU programmability.
- Documentation Gaps – Critical workflows were scattered across systems, and engineers struggled to understand why models failed to compile or how to optimize for TPU hardware.
- Internal Infrastructure – Work required navigating Google’s internal systems (bug trackers, changelists, internal search engines, go links) to locate SMEs and surface authoritative information.

## Approach

### 1. User Journeys: Structured docs around four critical workflows

I mapped out the end-to-end developer workflow into four critical stages:

1. **Build a Model** – Author in TensorFlow, train, evaluate quality.

2. **Port a Model** – Convert to TFLite, compile/lower to target hardware.

3. **Profile a Model** – Validate accuracy, measure performance KPIs.

4. **Deploy a Model** – Integrate with runtime, optimize, and run at scale.

This framework became the backbone of the SDK documentation.

### 2. Audience Segmentation

I identified three primary user types and aligned documentation strategy to their needs:

• **Novice Developers** – wanted “out-of-the-box” functionality.

• **Motivated Developers** – willing to adapt models and use SDK tools.

• **Advanced Developers** – required low-level TPU programmability.

### 3. Toolchain Documentation

For each tool (Compiler, Profiler, Simulator, Runtime, Numerics), I created:
• Conceptual overviews – what the tool is and when to use it.
• User guides – step-by-step workflows.
• Best practices – performance tuning and optimization tips.
• Sample code and troubleshooting – concrete examples with error handling.

### 4. Cross-Team Collaboration

• Partnered with SMEs across engineering to validate technical accuracy.
• Used bug tracking systems and changelists to manage documentation requests.
• Implemented process improvements for doc accountability and timely reviews.

## Deliverables

- SDK developer guides for build/port/profile/deploy
- Best practices + troubleshooting with sample snippets
- “What works on TPU” orientation and error-path guidance

## Impact

- Reduced model compilation confusion and turnaround
- Faster path from prototype to deployment
- Single, authoritative entry point for SDK users

## Skills / Tech

TensorFlow, SDK/API docs, developer workflows, information architecture, internal toolchains, ML perf/accuracy concepts.
