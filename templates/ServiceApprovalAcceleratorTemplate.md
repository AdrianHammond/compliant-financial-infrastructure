# Service Approval Accelerator (SAA) Template

_**Template Notes:**_

- _Examples within this template are included only to facilitate the demonstration of the correct formatting._
- _Use this section to provide a written description of anything unique to this SAA._

## 1. Baseline

_**Template Notes:**_

- _Text here may be omitted, or optionally used to provide any supplemental information related to the baseline._
- _We will aim to stick to CIS as much as possible, though the specific benchmark will be changed on a case-by-case basis._
- _Multiple benchmarks may be linked if required for full compliance coverage._

The policies included in the following document(s) are required for compliance,
unless otherwise noted in section 2: [Amendments to the Baseline](#2-amendments-to-the-baseline)

| Standard | Name | Link |
|---|---|---|
| CIS      | Kubernetes V1.23 Benchmark v1.0.1 | [downloads.cisecurity.org](https://downloads.cisecurity.org/#/) |

## 2. Amendments to the Baseline

_**Template Notes:**_

- _If anything in the above baseline is to be excluded or handled differently, provide details in this section_
_following the format demonstrated in section 3: [Extensions to the Baseline](#3-extensions-to-the-baseline)._
- _If no amendments are necessary, simply provide the following text:_

All guidelines provided by the aforementioned baseline are to be followed without modification or exception.

## 3. Extensions to the Baseline

_**Template Notes:**_

- _Use this section to provide a summary of any additional measures that must be taken in addition to the baseline._
- _Formatting for extensions and amendments should imitate the CIS benchmark format as closely as possible._
- _The example below is actually covered by a different CIS control, 5.5.1,_
_but I'm adding a custom version here simply for demonstration of formatting._

### 1. Ensure deployment from an unauthorized container registry is denied

**Profile Applicability:**
- Level 2 - Master Node

**Description:**

- Only accept known, authorised container registries for pod deployments.

**Rationale:**

- Containers deployed using unauthorized registries may introduce insecure images that are not approved for firm use.
To mitigate this risk, only trusted registries with approved images should be allowed.

**Impact:**

- You reject any deployment that requests an unauthorized registry.

**Audit:**

- Attempt to deploy a pod using an image from `docker.io`.

**Remediation:**

- Follow the Kubernetes documentation and setup image provenance, or restrict access to unauthorized registries on the network.

**References:**
  1. https://kubernetes.io/docs/reference/access-authn-authz/admission-controllers/#imagepolicywebhook
  1. https://stackoverflow.com/questions/54463125/how-to-reject-docker-registries-in-kubernetes
