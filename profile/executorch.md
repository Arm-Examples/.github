[**Arm Examples**](https://github.com/Arm-Examples/) » [**Edge AI**](EdgeAI.md) » **ExecuTorch on real hardware**

# Create an ExecuTorch application for real hardware

## Introduction

![ExecuTorch workflow](ExecuTorch.png "ExecuTorch workflow for Arm Cortex-M and Ethos-U")

An Edge AI application is more than an ML model. The model must fit the target's
memory architecture, use its Ethos-U configuration, connect to application and
sensor code, and run reliably on the real device.

The [CMSIS-Executorch template](https://github.com/Arm-Examples/CMSIS-Executorch)
provides a working starting point for this integration. It connects a PyTorch
model to the ExecuTorch runtime, the Arm Ethos-U backend, CMSIS-Toolbox, and the
[CMSIS-Ethos-U pack](https://www.keil.arm.com/packs/cmsis-ethos-u-arm/overview/).
The template includes Corstone reference targets, but its workflow applies to
all Ethos-U configurations.

The [CMSIS Developer Assistant](https://marketplace.visualstudio.com/items?itemName=Arm.cmsis-developer-assistant)
helps adapt that starting point to real hardware. It gives an AI coding agent
access to CMSIS project information, software-pack documentation, the build
system, and the CMSIS Debugger. The agent can therefore help select the correct
device support, create a board layer, configure a debug probe, build and program
the application, and inspect its behavior on the connected target.

This tutorial takes you through that workflow.

## How the pieces fit together

![Target-aware ML deployment](ExecuTorch_MLOps.png "Target-aware ML deployment with CMSIS-Toolbox")

The target description and the ML deployment flow meet at a generated
`*.cbuild-mlops.yml` file:

- The device family pack describes the processor, memory, and device-specific
  Ethos-U and Vela configuration.
- The CMSIS solution adds the application, model, build, and run information.
- CMSIS-Toolbox resolves this information for the selected target and writes
  the MLOps description.
- `create_ai_layer.py` uses that description to quantize and export the model,
  delegate supported operators to Ethos-U, and generate the target-specific AI
  software layer.
- CMSIS-Toolbox builds the AI layer together with the embedded application.

This preserves the hardware-specific information needed for optimization while
keeping the deployment steps consistent across devices.

## What you need

- A development board or custom device with an Arm Cortex-M processor and an
  Ethos-U55, Ethos-U65, or Ethos-U85 NPU.
- A CMSIS device family pack for the device and either an existing board support
  layer or enough board information to create one.
- A CMSIS-DAP, ST-Link, ULINKplus, or J-Link debug connection supported by the
  [CMSIS Debugger](https://marketplace.visualstudio.com/items?itemName=Arm.vscode-arm-debugger).
- [Keil Studio for VS Code](https://marketplace.visualstudio.com/items?itemName=Arm.keil-studio-pack),
  the VS Code Python extension, and the CMSIS Developer Assistant.
- An MCP-compatible AI coding agent configured by the Developer Assistant.
- A PyTorch model and representative calibration inputs.

Install the [CMSIS Developer Assistant from the VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=Arm.cmsis-developer-assistant),
then reload VS Code.

## 1. Create a repository from the template

Open [CMSIS-Executorch](https://github.com/Arm-Examples/CMSIS-Executorch) and
select **Use this template**. Clone the new repository and open its folder in
VS Code.

Allow the Arm Tools Environment Manager to finish installing the tools from
`vcpkg-configuration.json`. Then use **Terminal > Run Task > Create Python
environment (uv)**. The task creates `.venv` and installs the Python packages
needed to export an ExecuTorch model.

Before changing the target, build and run the default Corstone-320/Ethos-U85
configuration once. This separates template or tool-installation issues from
the hardware port.

## 2. Connect the CMSIS Developer Assistant

Install and enable the CMSIS Developer Assistant, then run **CMSIS Developer
Assistant: Configure Agents and Skills** from the VS Code Command Palette.
Select your AI agent and install the CMSIS project skills for this workspace.
The extension supplies the live-debugging, board-layer, pack-documentation, and
help skills needed later in the workflow.

Check that the agent can see the project before asking it to make changes:

```text
Inspect this CMSIS-Executorch workspace. Identify the loaded solution, active
target, required packs, compiler, and available debug adapters. Do not modify
the project yet.
```

The answer should describe the existing Corstone target and confirm access to
the CMSIS solution tools. If more than one VS Code window is open, tell the
agent which workspace to use.

## 3. Add the real hardware target

Give the agent the exact board name and revision, or the device part number for
custom hardware. Also state whether you want to keep the supplied Corstone
targets. For example:

```text
Add <board and revision> as a new target to this CMSIS-Executorch template.
Keep the existing Corstone targets. Verify the exact device, DFP, BSP, and
Ethos-U configuration from the installed packs and pack documentation before
editing the solution. Show me the proposed target and board-layer changes.
```

The agent can use the CMSIS project and pack-documentation skills to resolve a
fuzzy product name to the exact CMSIS board or device identifier. It should add
the required pack declarations and a target type to a `*.csolution.yml` file.

If no compatible packaged board layer exists, ask the agent to create one:

```text
Create a board layer for the new target. Ask me for any facts that cannot be
read from the packs: debugger, STDIO transport, memory regions, startup
strategy, and RTOS use. Reuse the vendor BSP where possible.
```

For an ExecuTorch application, review these parts of the resulting layer:

- device startup and system clock initialization;
- the CMSIS-Ethos-U driver component matching the NPU family;
- NPU interrupt routing and cache-maintenance hooks;
- model, arena, and command-stream placement in accessible memory;
- STDOUT for diagnostics;
- optional CMSIS-RTOS2 integration; and
- the device-specific Vela system and memory configuration.

Do not copy the Corstone memory map into a hardware target. The linker regions
and Vela memory mode must describe the real device.

## 4. Configure programming and debugging

Connect and power the board, then ask the agent to configure the probe:

```text
Configure this target for Load & Debug with my <CMSIS-DAP, ST-Link,
ULINKplus, or J-Link> probe. Verify the generated build-and-run description,
program the image, stop at main, and confirm that the target is responsive.
```

The CMSIS Solution extension generates the debugger configuration. The
Developer Assistant uses the same build, load, and debug actions as the VS Code
VS Code CMSIS view, so the manual and agent-driven workflows stay aligned.

At this point, use a minimal application or the unchanged template model. First
prove startup, programming, breakpoint control, and console output. Model
conversion is much easier to diagnose after basic board bring-up works.

## 5. Integrate your PyTorch model

Replace the starter network in `model/model.py` with your model entry point.
Keep the interface expected by `create_ai_layer.py`, including representative
calibration inputs. Calibration data should cover the operating range seen by
the real application; placeholder random data may produce a technically valid
but inaccurate quantized model.

Ask the agent to review the model integration before exporting it:

```text
Review model/model.py and the application input/output handling for my model.
Check tensor shapes, data types, calibration inputs, output interpretation,
and whether the required operators are supported by the ExecuTorch Arm
backend. Suggest changes, but do not export the model yet.
```

Also adapt `src/app_main.cpp` to acquire or prepare the real input tensor and to
consume the output. Keep a deterministic test input initially; connect live
sensors only after the model produces the expected result on the board.

## 6. Generate the target-specific AI layer

Select the new solution and target in the VS Code CMSIS view. Run a setup operation so
CMSIS-Toolbox resolves the device and application information:

```bash
cbuild setup <solution>.csolution.yml --active <target> --packs
```

Inspect the generated `<solution>.cbuild-mlops.yml`. Confirm that its processor,
NPU family, MAC configuration, Vela system configuration, memory mode, model,
and run information match the real hardware.

Now run **Terminal > Run Task > Create AI layer**, or use:

```bash
.venv/bin/python create_ai_layer.py <solution>.cbuild-mlops.yml
```

On Windows, use `.venv\Scripts\python.exe`. The command regenerates
`ai_layer/` for the selected target. Repeat this step whenever the model, target,
or Vela configuration changes.

## 7. Build, program, and run on the board

Build the new target from the VS Code CMSIS view or command line:

```bash
cbuild <solution>.csolution.yml --active <target>
```

Then ask the Assistant to exercise the complete path:

```text
Build, load, and debug the active target. Stop at app_main, verify the reported
Ethos-U product and MAC configuration, run one inference, and report the output
and any driver or Vela errors. Use the debugger to investigate failures; do not
add temporary logging unless live inspection cannot answer the question.
```

The application should initialize the NPU, load the embedded `.pte` program,
execute the delegated graph, and print a result. A useful first acceptance test
compares the target output against a known result from the host-side model.

## 8. Debug integration problems with target evidence

The Developer Assistant can halt the processor and inspect the real system
instead of guessing from symptoms. Useful follow-up requests include:

```text
The application entered HardFault. Decode the fault status registers, inspect
the faulting instruction and stack frame, and identify the invalid access.
```

```text
Set breakpoints around Ethos-U initialization and inference. Verify the NPU
base address, command-stream address, tensor buffers, and interrupt handling.
```

```text
Compare the linker map with the model and tensor-pool sizes. Check that every
buffer is in memory accessible by both the Cortex-M processor and the NPU and
that required alignment and cache maintenance are correct.
```

Typical porting failures are incorrect memory regions, a Vela configuration
that does not match the device, missing cache maintenance, incorrect interrupt
routing, insufficient tensor or method-pool memory, and application tensors
whose shape or type differs from the exported program.

## 9. Build an SDS test harness

![Edge AI development loop](EdgeAI_Loop.png "Target evidence closes the Edge AI development loop")

After deterministic inference works, use the
[Synchronous Data Stream Framework](https://github.com/ARM-software/SDS-Framework)
to make the input and output of the algorithm reproducible. SDS can play a
recorded sensor, audio, or image stream into an application and record the
algorithm output at the same time. The same files can drive an FVP during early
development and the real board later.

### Define the streams before writing target code

Start with one stream for each boundary that a test must control or observe. A
vision application might use:

| Stream | Direction | Contents |
|---|---|---|
| `CameraIn` | Playback to the application | Preprocessed camera frame presented to the model |
| `ModelOut` | Record from the application | Raw logits, heatmaps, boxes, or keypoints |
| `Result` | Record from the application | Post-processed result used by the product |

Keep raw model output and post-processed application output separate. This lets
you determine whether a regression came from model conversion or from the C/C++
post-processing code. Define each stream's tensor shape, data type, byte order,
sample rate or frame rate, and timeslot relationship in its SDS metadata.

Ask the agent to implement the harness explicitly:

```text
Add an SDS test harness to this application. Use CameraIn as the playback
stream and record ModelOut and Result. Add the ARM::SDS pack, the SDS framework
components, stream metadata, an SDSIO layer for the FVP, and host-side tools to
create inputs and inspect outputs. Keep the normal camera path selectable for
later hardware use. Stop cleanly at end-of-stream and make the test suitable
for unattended CI.
```

The application loop should read one input record, run exactly one inference,
write output records with the same timeslot, and continue until SDS reports end
of stream. Do not hide image preprocessing in the host tool unless the real
camera pipeline performs the identical operation. The playback data should
exercise the same tensor boundary that the hardware path uses.

### Configure playback on an FVP

For an FVP, use the SDS VSI interface. The Python VSI implementation performs
the file playback and recording, so a separate SDSIO-Server process is not
required. Point `SDSIO_FVP` at an absolute path to a `*.sdsio.yml` control file,
or place that control file in the simulator working directory.

A control file groups the test cases and selects their labels. For example:

```yaml
sdsio:
  workdir: ./recordings/pose
  recdir: ./results/pose
  play:
    - step: "Pose regression images"
      labels: [ski, surf, mirror, group, negative]
```

With this convention, playback reads files such as `CameraIn.ski.sds` and
records files such as `ModelOut.ski.p.sds`. The `.p` indicates output captured
during playback. Also retain `sdsio.log`; it proves which streams and labels the
FVP opened and whether playback reached end-of-stream.

Ask the agent to automate the complete run:

```text
Run every SDS playback step on the FVP. Fail on an FVP error, missing output,
unexpected tensor shape, or a result outside the declared tolerance. Save the
FVP log, sdsio.log, raw SDS output, a machine-readable result summary, and a
rendered image for every test case.
```

### Compare results and store visual evidence

Run the same inputs through a host-side PyTorch reference and the FVP build.
Comparison must account for quantization: use an application-level tolerance
instead of requiring byte-identical floating-point output. For pose estimation,
use keypoint distance and confidence; for classification, compare the expected
class and score range; for detection, use class, score, and box overlap.

Create a result directory that CI can upload as an artifact:

```text
test-results/
  summary.json
  fvp.log
  sdsio.log
  raw/
  images/
```

Each rendered image should show the original input beside an overlay made from
the FVP result, with the test label, pass/fail state, and relevant measurements.
Include negative images with no valid subject; they often expose false positives
that are not visible in happy-path tests.

### Move the same tests to hardware

When the board arrives, keep the stream names, metadata, playback files,
comparison code, and acceptance thresholds. Replace the FVP SDSIO layer with a
hardware transport such as USB, RTT, or a network socket and run
`sdsio-server.py` on the host. This changes the transport, not the test case.
After the playback tests pass, switch to record mode to capture real camera or
sensor data and add difficult field cases to the regression set.

## Example: prompt to pose-estimation tests

The following single prompt illustrates how the Developer Assistant can be
given an application goal, a temporary virtual target, and explicit test
evidence requirements:

```text
Starting from cmsis-executorch, create a pose detection model on the Alif E7
AppKit. Please do all tests on FVP until we have the board later. Use SDS to
feed in and out the test harness. Store images of the tests.
```

In this example, the agent found
[Lightweight OpenPose for PyTorch](https://github.com/ModelBunker/Lightweight-OpenPose-PyTorch)
and adapted its MobileNet v1 backbone, CPM block, and initial OpenPose stage for
ExecuTorch and Ethos-U. The exported single-person model accepts an NHWC RGB
camera frame and produces 19 stride-8 heatmaps: 18 body keypoints plus
background. Normalization and the checkpoint's BGR channel ordering were folded
into the graph so that the embedded application could pass camera pixels across
a simple quantized boundary.

The agent omitted the part-affinity-field output used for multi-person assembly
and made the refinement-stage count configurable. With no refinement stages,
the model fit the available application MRAM; each added stage increased model
size. This is a good example of adapting a research model to the constraints and
actual product requirement rather than exporting the upstream network unchanged.

SDS then fed a set of labeled images into the FVP and recorded the heatmaps and
decoded keypoints. The result renderer stored side-by-side input and skeleton
overlays, including a negative image with no person. Those images made failures
visible while the raw SDS files and numeric summary kept the test suitable for
automation.

The important pattern is reusable:

1. state the application and hardware goal;
2. require the agent to justify the selected model and license;
3. define the embedded input and output tensor boundary;
4. use SDS playback to make test inputs deterministic;
5. compare host and FVP results using task-specific tolerances; and
6. preserve logs, raw outputs, summaries, and rendered evidence.

## Close the loop with real data

The productive loop is:

1. describe the selected hardware accurately;
2. generate an optimized model and software layer for that target;
3. build and run the complete application;
4. collect evidence from the real device; and
5. feed the results and captured data into the next model or application
   iteration.

The model is only one component. Success means that the complete application
works with the target's real memory, peripherals, timing, and data.

## What to keep and what to replace

| Keep from the template | Adapt for your application |
|---|---|
| Three-step CMSIS/MLOps/build flow | Board, device, and debugger configuration |
| ExecuTorch runtime and Ethos-U backend components | PyTorch model and calibration data |
| `create_ai_layer.py` and generated AI-layer structure | Input pipeline and output interpretation |
| CMSIS-Ethos-U driver integration pattern | Memory regions, cache policy, and interrupts |
| CI structure and FVP reference targets | Hardware tests and captured real-world data |

## Worked example: an Alif E7 traffic counter

The [CMSIS ExecuTorch traffic counter](https://github.com/MatthiasHertelArm/cmsis-executorch-traffic-counter)
shows what a complete application derived from the template can become. It runs
an Ultralytics YOLO26n detector on the Ethos-U55-256 of an Alif Ensemble E7
AppKit while a Cortex-M55 tracks and counts vehicles crossing a line in the
camera image.

The project extends the template with the real board and memory configuration,
camera and display pipelines, application-side tracking, an embedded UI, and
SDS recording and playback over USB. It is a useful reference for four parts of
your own port:

- adding a vendor device and board target to the CMSIS solution;
- turning a larger PyTorch vision model into a target-specific AI layer;
- dividing work between the Ethos-U NPU and Cortex-M application code; and
- capturing real model inputs and replaying them as repeatable hardware tests.

Use it as an implementation reference rather than a second starting template:
create your application from CMSIS-Executorch, then bring across only the board,
pipeline, SDS, or test patterns that fit your hardware.

## Further reading

- [CMSIS-Executorch template](https://github.com/Arm-Examples/CMSIS-Executorch)
- [CMSIS ExecuTorch traffic counter](https://github.com/MatthiasHertelArm/cmsis-executorch-traffic-counter)
- [CMSIS Developer Assistant on the VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=Arm.cmsis-developer-assistant)
- [CMSIS-Ethos-U documentation](https://arm-software.github.io/CMSIS-Ethos-U/)
- [ExecuTorch Arm Ethos-U backend](https://docs.pytorch.org/executorch/main/backends-arm-ethos-u.html)
- [CMSIS-Toolbox MLOps information](https://open-cmsis-pack.github.io/cmsis-toolbox/build-overview/#mlops-information)
- [Synchronous Data Stream Framework](https://github.com/ARM-software/SDS-Framework)
- [Lightweight OpenPose for PyTorch](https://github.com/ModelBunker/Lightweight-OpenPose-PyTorch)
