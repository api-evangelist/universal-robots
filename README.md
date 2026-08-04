# Universal Robots (universal-robots)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Universal Robots is a Danish collaborative-robot (cobot) manufacturer headquartered in Odense, Denmark, founded in 2005 and acquired by Teradyne in 2015 for USD 285 million. With more than 100,000 cobots sold and a 40–50% share of the global cobot market, Universal Robots is the category's market leader. Unlike most industrial-robot vendors, Universal Robots ships an open, well-documented developer surface — RTDE, Dashboard Server, Primary/Secondary Client Interface, XML-RPC, URScript, the URCap SDK (PolyScope 5), and the PolyScope X URCap SDK — backed by official C++, Python, and ROS / ROS 2 client libraries on GitHub.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/universal-robots/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

- Robotics, Collaborative Robots, Cobots, Industrial Automation, Manufacturing, PolyScope, PolyScopeX, URCaps, URScript, RTDE, ROS, ROS 2, Teradyne, Danish, Hardware

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## Product Lines

| Generation | Model | Payload | Reach |
|---|---|---|---|
| e-Series | UR3e | 3 kg | 500 mm |
| e-Series | UR7e | 7.5 kg | 850 mm |
| e-Series | UR12e | 12.5 kg | 1300 mm |
| e-Series | UR16e | 16 kg | 900 mm |
| UR Series | UR8 Long | 10 kg | 1750 mm |
| UR Series | UR15 | 17.5 kg | 1300 mm |
| UR Series | UR18 | 18 kg | 950 mm |
| UR Series | UR20 | 25 kg | 1750 mm |
| UR Series | UR30 | 35 kg | 1300 mm |

## APIs and Interfaces

Universal Robots does not publish an HTTP/REST API or OpenAPI specification. Programmatic access is exclusively via documented TCP socket protocols and SDKs.

### Real-Time Data Exchange (RTDE)
Synchronous binary TCP protocol on port 30004 streaming robot state at the controller cycle (500 Hz on e-Series, 125 Hz on CB3) and accepting writeable inputs. Canonical integration point for vision, force/torque, OEE telemetry, and ROS / ROS 2 drivers.

- [Documentation](https://docs.universal-robots.com/)
- [RTDE Guide](https://www.universal-robots.com/articles/ur/interface-communication/real-time-data-exchange-rtde-guide/)
- [SDK — RTDE Python Client Library](https://github.com/UniversalRobots/RTDE_Python_Client_Library)
- [SDK — C++ Client Library](https://github.com/UniversalRobots/Universal_Robots_Client_Library)
- [SDK — RTDE ROS 2 Publisher](https://github.com/UniversalRobots/RTDE_ROS2_Publisher)

### Dashboard Server
Plain-text TCP command interface on port 29999 for power, program load/play, safety state, and installation management. The easiest remote-control entry point for shop-floor MES integration.

- [Dashboard Server (CB Series)](https://www.universal-robots.com/articles/ur/dashboard-server-cb-series-port-29999/)
- [Dashboard Server (e-Series)](https://www.universal-robots.com/articles/ur/dashboard-server-e-series-port-29999/)
- [SDK — C++ Client Library](https://github.com/UniversalRobots/Universal_Robots_Client_Library)

### Primary and Secondary Client Interface
Streaming binary interfaces on ports 30001 (Primary, 10 Hz, includes configuration) and 30002 (Secondary, 10 Hz). The Secondary interface is the recommended channel for sending URScript at runtime.

- [Remote Control via TCP/IP](https://www.universal-robots.com/articles/ur/interface-communication/remote-control-via-tcpip/)
- [Overview of Client Interfaces](https://www.universal-robots.com/articles/ur/interface-communication/overview-of-client-interfaces/)
- [SDK — C++ Client Library](https://github.com/UniversalRobots/Universal_Robots_Client_Library)

### Real-Time Interface
Binary state interface on port 30003 emitting robot state at the controller cycle. Predates RTDE; new integrations should prefer RTDE.

- [Remote Control via TCP/IP](https://www.universal-robots.com/articles/ur/interface-communication/remote-control-via-tcpip/)

### XML-RPC
URScript's `xmlrpc_factory` primitive lets a robot program call out to any user-hosted XML-RPC server mid-execution. Canonical pattern for delegating vision, business logic, or database lookups from a robot program to an off-board service.

- [XML-RPC Tutorial](https://www.universal-robots.com/articles/ur/interface-communication/xml-rpc-tutorial/)

### URScript
Universal Robots' purpose-built scripting language for cobot motion, I/O, and process control. Authored in PolyScope, streamed over the Secondary Client Interface, or generated by ROS 2 driver and MoveIt.

- [URScript Page](https://www.universal-robots.com/products/ur-developer-suite/urscript/)
- [URScript Examples](https://github.com/UniversalRobots/URScript_Examples)

### URCap SDK (PolyScope 5)
Java-based extension framework that powers Universal Robots' UR+ ecosystem of certified third-party integrations. URCaps add program nodes, installation screens, daemons, and driver contributions (grippers, screwdrivers, vision).

- [URCap Page](https://www.universal-robots.com/products/ur-developer-suite/urcap/)
- [URCap Samples](https://github.com/UniversalRobots/URCap-Samples)
- [UR+ Marketplace](https://www.universal-robots.com/plus/)

### PolyScope X URCap SDK
TypeScript/HTML extension framework for PolyScope X, the next-generation teach-pendant OS that ships on UR15/UR20/UR30 and newer cobots. PolyScope X URCaps are Docker-containerised for sandboxing and replace the legacy Java URCap model.

- [PolyScope X Documentation](https://docs.universal-robots.com/polyscopex/)
- [PolyScope X URCap SDK](https://github.com/UniversalRobots/PolyScopeX_URCap_SDK)

## Official GitHub Repositories

Universal Robots maintains an unusually broad open-source presence at [github.com/UniversalRobots](https://github.com/UniversalRobots):

- [Universal_Robots_Client_Library](https://github.com/UniversalRobots/Universal_Robots_Client_Library) — C++ library exposing RTDE, Dashboard, Primary/Secondary, and motion streaming
- [Universal_Robots_ROS2_Driver](https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver) — ROS 2 driver (CB3 and e-Series)
- [Universal_Robots_ROS_Driver](https://github.com/UniversalRobots/Universal_Robots_ROS_Driver) — ROS 1 driver (CB3 and e-Series)
- [RTDE_Python_Client_Library](https://github.com/UniversalRobots/RTDE_Python_Client_Library) — RTDE Python client and examples
- [Universal_Robots_ROS2_Description](https://github.com/UniversalRobots/Universal_Robots_ROS2_Description) — URDF descriptions for ROS 2
- [Universal_Robots_ROS2_Gazebo_Simulation](https://github.com/UniversalRobots/Universal_Robots_ROS2_Gazebo_Simulation) — Gazebo simulation
- [Universal_Robots_Isaac_Driver](https://github.com/UniversalRobots/Universal_Robots_Isaac_Driver) — NVIDIA Isaac SDK driver
- [Universal_Robots_ExternalControl_URCap](https://github.com/UniversalRobots/Universal_Robots_ExternalControl_URCap) — PolyScope 5 URCap for ROS / ROS 2 drivers
- [Universal_Robots_ExternalControl_URCapX](https://github.com/UniversalRobots/Universal_Robots_ExternalControl_URCapX) — PolyScope X URCap for ROS / ROS 2 drivers
- [PolyScopeX_URCap_SDK](https://github.com/UniversalRobots/PolyScopeX_URCap_SDK) — PolyScope X URCap SDK
- [URCap-Samples](https://github.com/UniversalRobots/URCap-Samples) — URCap sample projects
- [URScript_Examples](https://github.com/UniversalRobots/URScript_Examples) — URScript examples and snippets
- [ModbusExamples](https://github.com/UniversalRobots/ModbusExamples) — Modbus communication examples
- [Universal_Robots_ROS_as_a_Service_URCap](https://github.com/UniversalRobots/Universal_Robots_ROS_as_a_Service_URCap) — rosbridge-backed ROS access from inside PolyScope

## Resources

- [Website](https://www.universal-robots.com/)
- [Developer Suite](https://www.universal-robots.com/products/ur-developer-suite/)
- [Documentation](https://docs.universal-robots.com/)
- [GitHub](https://github.com/UniversalRobots)
- [Forum](https://forum.universal-robots.com/)
- [UR+ Marketplace](https://www.universal-robots.com/plus/)
- [Academy](https://academy.universal-robots.com/)
- [Partner Portal](https://partners.universal-robots.com/)
- [Support](https://www.universal-robots.com/support/)
- [Downloads](https://www.universal-robots.com/download/)
- [About](https://www.universal-robots.com/about-universal-robots/)
- [Newsroom](https://www.universal-robots.com/news-centre/)
- [Careers](https://www.universal-robots.com/careers/)
- [Contact](https://www.universal-robots.com/contact/)
- [Parent — Teradyne](https://www.teradyne.com/)
- [Sibling — Mobile Industrial Robots (MiR)](https://www.mobile-industrial-robots.com/)
- [LinkedIn](https://www.linkedin.com/company/universal-robots/)
- [YouTube](https://www.youtube.com/user/UniversalRobots)
- [Twitter](https://twitter.com/universal_robot)

## Maintainer

Kin Lane — kin@apievangelist.com
