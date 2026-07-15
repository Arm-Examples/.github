[**Arm Examples**](https://github.com/Arm-Examples/) » **CI/CD**

# CI/CD (Continuous Integration / Continuous Delivery)

Modern embedded software development requires automated workflows that ensure code quality, enable rapid iteration, and support collaborative development. CI/CD practices bring these capabilities to embedded systems, helping teams deliver reliable firmware faster while maintaining high quality standards.

[MDK](https://www.keil.arm.com/keil-mdk/) includes tools to establish comprehensive CI/CD workflows that include [automated builds](#automated-build-test) as well as unit testing and integration testing on [simulation models](#arm-fixed-virtual-platforms-fvp) or [target hardware](#hil-testing-with-pyocd). [Keil Studio](https://marketplace.visualstudio.com/items?itemName=Arm.keil-studio-pack) is based on VS Code that integrates Git features and offers several VS Code extensions for static code analysis. The [CMSIS-Toolbox](https://open-cmsis-pack.github.io/cmsis-toolbox/) is a command-line interface for building embedded applications, enabling seamless integration with popular CI/CD platforms (like GitHub Actions). Integration with static code analysis tools (e.g. MISRA checking) is achieved with standard database files that third-party tools can consume.

![CI/CD Process Overview](CICD_Overview.png "CI/CD Process Overview")

[GitHub Actions](https://docs.github.com/en/actions) execute build or test jobs on runners. A `*.yml` file in a `.github/workflows` directory of a repository defines a set of tasks such as building and testing pull requests.

The repositories on [github.com/Arm-Examples](https://github.com/Arm-Examples) use topics to label:

- [cicd](https://github.com/search?q=topic%3Acicd+org%3AArm-Examples+fork%3Atrue&type=repositories) – repository with automated workflows.
- [simulation](https://github.com/search?q=topic%3Asimulation+org%3AArm-Examples+fork%3Atrue&type=repositories) – repository with test on simulation.
- [hardware](https://github.com/search?q=topic%3Ahardware+org%3AArm-Examples+fork%3Atrue&type=repositories) – repository with test on hardware target.

[Arm-Software/cmsis-actions](https://github.com/ARM-software/cmsis-actions) are reusable workflows that let you install tools and active software licenses. Use the instructions of these actions to enable other CI/CD systems such as Azure DevOps or GitLab.

## CI/CD Capabilities for Embedded Development

The underlying build system of [Keil Studio](https://www.keil.arm.com/) uses the [CMSIS-Toolbox](https://open-cmsis-pack.github.io/cmsis-toolbox/) and CMake. [GitHub-hosted runners](https://docs.github.com/en/actions/using-github-hosted-runners/using-github-hosted-runners/about-github-hosted-runners) provide virtual machines for automated build and execution tests using simulation models, while [self-hosted runners](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners/about-self-hosted-runners) enable testing on actual target hardware. [CI](https://en.wikipedia.org/wiki/Continuous_integration) is streamlined with:

- Consistent tool installation based on a single [`vcpkg-configuration.json`](https://github.com/Arm-Examples/Hello_World/blob/main/vcpkg-configuration.json) file for desktop and CI environments.
- CMSIS solution files (`*.csolution.yml`) that enable seamless builds in CI, for example using GitHub actions.
- [Run and Debug Configuration](https://open-cmsis-pack.github.io/cmsis-toolbox/build-overview/#run-and-debug-configuration) for pyOCD that uses a single configuration file `*.cbuild-run.yml`.

### Automated Build Test

The [CMSIS-Toolbox](https://open-cmsis-pack.github.io/cmsis-toolbox/) enables reproducible builds across different environments using the *csolution project* files that define build configurations, dependencies, and target devices. Build automation ensures that every code change is validated consistently, catching integration issues early.

> Badges with a label **Build** indicate [GitHub actions](https://github.com/features/actions) that run build tests using the CMSIS-Toolbox.
>
> [![Build Test](https://img.shields.io/github/actions/workflow/status/Arm-Examples/Safety-Example-Infineon-T2G/Build_T2G_Release.yaml?logo=arm&logoColor=0091bd&label=Build)](https://github.com/Arm-Examples/Safety-Example-Infineon-T2G/blob/main/.github/workflows/Build_T2G_Release.yaml "Build Test")

### Automated Execution Test

Effective embedded development incorporates various testing strategies:

- **Unit testing** where code is tested primarily at function level using a test framework like Unity.
- **Integration testing** where multiple components are combined and interfaces between these components are verified.
- **System testing** where the complete system is tested against the requirements.

[MDK](https://www.keil.arm.com/keil-mdk/) supports unit testing and integration testing on target systems with:

- **Arm Fixed Virtual Platforms (FVP)** are simulation models to test without physical devices, accelerating feedback cycles.
- **Hardware-in-the-Loop (HIL) Testing** with debug adapters to execute tests on actual target hardware to verify real-world behavior.

CI pipelines may store build artifact files, reports, and may further automate firmware packaging, versioning, and deployment processes, ensuring traceability from source code to deployed binaries.

## Arm Fixed Virtual Platforms (FVP)

[Arm FVPs](https://arm-software.github.io/AVH/main/simulation/html/index.html) are functionally accurate simulation models of Arm-based Cortex-M CPUs and Corstone-3xx subsystems. [Virtual Interfaces](https://arm-software.github.io/AVH/main/simulation/html/group__arm__cmvp.html) in Arm FVPs implement various CPU peripherals that allow to use external resources for stimulating the firmware application. Several virtual interfaces connect to Python for flexible scripting in test automation.

> Badges with a label **Test** or **Simulation** indicate [GitHub actions](https://github.com/features/actions) that run tests on virtual hardware with FVP simulation models.
>
>[![Execution Test](https://img.shields.io/github/actions/workflow/status/Arm-Examples/SDS-Examples/Test_ST_KeywordSpotting.yml?logo=arm&logoColor=0091bd&label=Test)](https://github.com/Arm-Examples/SDS-Examples/blob/main/.github/workflows/Test_ST_KeywordSpotting.yml)

## HIL Testing with pyOCD

[Hardware-in-the-Loop (HIL)](https://en.wikipedia.org/wiki/Hardware-in-the-loop_simulation) testing is enabled with [self-hosted GitHub runners](RPI_GH_Runner.md) that connect to Linux systems equipped with debug probes. Build artifacts (firmware images) are generated through automated build tests on GitHub-hosted runners, then deployed to self-hosted runners where pyOCD downloads the firmware to target hardware and executes the test suite.

![HIL Integration](https://raw.githubusercontent.com/Arm-Examples/Safety-Example-Infineon-T2G/main/Doc/CI_HIL.png "HIL Integration")

> Badges with a label **Run** or **HIL** indicate [GitHub actions](https://github.com/features/actions) that run tests on actual target hardware with self-hosted GitHub runners.
>
>[![Run Test](https://img.shields.io/github/actions/workflow/status/Arm-Examples/Safety-Example-STM32/Run_NUCLEO_H563ZI_Release.yml?logo=arm&logoColor=0091bd&label=Run)](https://github.com/Arm-Examples/Safety-Example-STM32/blob/main/.github/workflows/Run_NUCLEO_H563ZI_Release.yml)
[![HIL Test](https://img.shields.io/github/actions/workflow/status/Arm-Examples/Safety-Example-STM32/Run_NUCLEO_H563ZI_Release.yml?logo=arm&logoColor=0091bd&label=HIL)](https://github.com/Arm-Examples/Safety-Example-STM32/blob/main/.github/workflows/Run_NUCLEO_H563ZI_Release.yml)

See [Setup of Raspberry Pi as Self-Hosted GitHub Runner](RPI_GH_Runner.md) for more information.
