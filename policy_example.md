# Simple Policy Description Example
*March 2025*

Note: this is a simple example open source policy collated from multiple sources. It is provided "as-is", for the purposes of illustrating open source policy usage in automation setting.

SPDX-FileCopyrightText: 2024-2025 Double Open Oy <support@doubleopen.org>
SPDX-FileCopyrightText: 2022-2023 HH Partners, Attorneys-at-law Ltd <doubleopen@hhpartners.fi>
SPDX-License-Identifier: CC-BY-4.0

## Table of Contents
1. [Policy Principles](#policy-principles)
   - [Main Licensing](#main-licensing)
     - [Product XXX](#product-xxx)
     - [Product YYY](#product-yyy)
     [Approach to Copyleft](#approach-to-copyleft)
   -   [Product XXX](#product-xxx-1)
   -   [Product YYY](#product-yyy-1)
     [Software Interaction Types](#software-interaction-types)
   - [Preferably Fully Open Source Dependencies](#preferably-fully-open-source-dependencies)
     [Investigating and Classifying Licenses](#investigating-and-classifying-licenses)
2. [Policy Rules](#policy-rules)
   - [License Category Based Rules](#license-category-based-rules)
   - [License Property Based Rules](#license-property-based-rules)
3. [Version History](#version-history)

---

## Policy Principles
### Main Licensing
#### Product XXX
The main license of the project is a proprietary license, and the product software copies are distributed to customers. Therefore, any third-party dependency licenses must be compatible with a proprietary license being distributed to customers, considering the applicable software interaction. Permissive licensed dependencies are generally unproblematic, while copyleft license dependencies are allowed only if the software interaction is appropriate. Non-open-source licensed dependencies must be inspected separately.

#### Product YYY
The main license of the project is a proprietary license, and the product is offered only as a SaaS service. Therefore, any open-source third-party dependency licenses are generally allowed, with the exception of licenses that include a network-clause. Non-open-source licensed dependencies must be inspected separately.

---

### Approach to Copyleft
#### Product XXX
As the product is distributed under a proprietary license, copyleft obligations in open-source licenses must be carefully controlled in relation to software interaction. All types of copyleft licenses are allowed as long as the interaction is appropriate. Additionally, potential incompatibilities between different copyleft licenses (e.g., GPL with other copyleft licenses) must be reviewed. Automatic review is acceptable where possible; otherwise, developers should manually review interactions.

##### Interaction Analysis
- **Code Change:** All open-source licenses except copyleft-strong, copyleft-LGPL, copyleft-module-level, and copyleft-file-level are allowed.
- **Separate Files:** All open-source licenses except copyleft-strong, copyleft-LGPL, and copyleft-module-level are allowed.
- **Separate Modules:** All open-source licenses except copyleft-strong and copyleft-LGPL are allowed.
- **Static Linking:** All open-source licenses except copyleft-strong and copyleft-LGPL are allowed. Copyleft-LGPL is allowed if additional compliance steps are taken.
- **Dynamic Linking:** All open-source licenses except copyleft-strong are allowed.
- **Looser Interaction:** All open-source licenses are allowed when software components interact over defined interfaces or are aggregated.

The product is software, and not a device, hence anti-tivo-properties in licenses are ok.

#### Product YYY
Since the product is not distributed but offered as a SaaS service, copyleft obligations do not trigger. Therefore, all copyleft licenses are allowed.

---

### Software Interaction Types
This section describes different types of software interaction and their implications for license compliance.

| Software Interaction Type | Description of interaction between OSS and Other Software |
|---------------------------|-------------|
| **Code Change** | Direct edits to OSS source code. Macro extensions and other methods of copying OSS code into source code files of Other Software.|
| **Separate Files** | OSS software remains in separate, unchanged files. All code changes  created (i.e. Other Software) are in separate source code files when compared to OSS. No code is copied from OSS files to files of Other Software. Code may be in the same module with code licenses in other ways.|
| **Separate Modules** | OSS is in a separate module within the same software project. All code changes created (i.e. Other Software) are in separate source code modules when compared to OSS. No code is copied from OSS modules to files of Other Software. |
| **Static Linking** | Linking Other Software code to an OSS library/component in a way that creates one executable binary file. Linking OSS to Other Software in the same way. Bundling Other Software with OSS library/component to create a file served to users, e.g. minified javascript files served to browsers. React native used in creation of mobile applications. |
| **Dynamic Linking** | Linking Other Software executable file to an OSS library when the executable is being executed. Package manager controlled Java dependencies, such as Maven, Gradle, Python Package Index or Node dependencies. |

### Preferably Fully Open Source Dependencies
It is the preference of the project that any third-party dependencies are licensed under a license permitting free use, copying, modification and redistribution, i.e., either a permissive license or some type of copyleft license. The OSI Open Source Definition gives indications as to whether the license is open source, but the project does not strictly bind the definition to OSI-accepted licenses only.

Licenses that are not considered open source should be picked up for further analysis as to whether there are additional restrictions or conditions incompatible with the aims and objectives of the project. The ORT evaluation engine can be configured to take these considerations into account by way of automatic violation alerts in certain conditions. Further information is provided below.

---

### Investigating and Classifying Licenses
We follow [Double Open's license categorization](https://github.com/doubleopen-project/policy-configuration/blob/main/license-classifications.yml), extending SPDX and ScanCode classifications.

### License Categories

#### Copyleft Strong
**Description:**
Open source license that requires you to license modifications, as well as any code that ends up in the same binary (including static linking and module modifications), as well as other code that is part of the same work, with the same strong copyleft license.

**Examples:**
GPL-2.0, GPL-3.0, AGPL-3.0, EUPL-1.0, EUPL-1.1, EUPL-1.2.

---

#### Copyleft LGPL
**Description:**
This category is for particular software interaction methods defined in the LGPL family of licenses, namely LGPL-2.0, LGPL-2.1, and LGPL-3.0. Loosely, if you statically link with an LGPL-licensed library, you need to provide for the recipient the option to modify the LGPL-licensed library and thereafter relink with your application.

**Examples:**
LGPL-2.0, LGPL-2.1, LGPL-3.0.

---

#### Copyleft Module Level
**Description:**
Open source license that requires you to license modifications made into the same software module with the same license as the original open-source software module. This also applies if you add code from this module to your own module.

**Examples:**
EPL-1.1, CPL-1.0.

---

#### Copyleft File Level
**Description:**
Open source license that requires you to license modifications made into the same file with the same license as the original open-source file. This also applies if you add code from this file to your own file.

**Example:**
MPL-2.0.

---

#### Permissive
**Description:**
Open source license that is made available under "non-copyleft" licenses. These generally require attribution of the included works and may include other obligations.

---

#### Free-Restricted
**Description:**
A permissive or open source-style license that contains restrictions regarding the usage of the work (for example, where a software is not allowed to be used in nuclear facilities) or the redistribution of the software (for example, where commercial redistribution of the software is not allowed without express permission). These licenses are not open source licenses since they do not include all the required freedoms.

---

#### Proprietary-Free
**Description:**
A proprietary-free license may not require a commercial license but has specific terms and conditions which the project is obligated to follow. Some of these terms and conditions are provided with or in the code or in clickable downloaded licenses.

**Examples:**
Sun Binary Code License Agreement, freely offered BSP.

---

#### Commercial
**Description:**
A license for third-party proprietary content offered under a direct commercial license between a supplier and a customer.

---

#### Public Domain
**Description:**
A dedication by which a work is placed into the public domain without any explicit obligations but which may have a notice that must be kept with the work per project policy. The match may be to software, code examples on a website, published public domain specifications, or another type of publication.

---

#### Source Available
**Description:**
A source-available license is released through a source code distribution model that includes arrangements where the source can be viewed, and in some cases modified, but without necessarily meeting the criteria to be called open-source.

---

#### Unstated
**Description:**
A statement used when no license is stated, but the content is likely under copyright.

**Common Examples:**
Code snippets from publications and websites (such as those from O'Reilly Media).

The majority of additional properties are:

### License Properties

#### Property: Network Clause
**Description:**
This license has specific terms that apply when the software is used or deployed over a network. Few licenses have such terms; examples include Affero GPL, EUPL-1.2 (and other versions), OSL, and the Common Public Attribution License (CPAL 1.0).

---

#### Property: Advertising Clause
**Description:**
This license requires a notice in certain advertisements for the product (typically those mentioning features of the licensed software) that the licensed software is being used.

---

#### Property: Non-Commercial
**Description:**
Licenses that add a restriction that prevents the use of the software for commercial purposes.

---

#### Property: Include in Notice File
**Description:**
Whether the license includes a notice obligation or similar, which can be fulfilled by adding the relevant copyright notices and the license text into the project/product notice file.

---

#### Include in Notice File (Temporary Workaround)
**Description:**
Same as above, as a temporary workaround for the category name not being configurable in ORT reports.
[GitHub Issue #8220](https://github.com/oss-review-toolkit/ort/issues/8220).

---

#### Property: Mark Modifications
**Description:**
The license includes an obligation to mark all modifications of licensed content.

---

#### Property: Antitivo Clause
**Description:**
This property means that the licensee/end user must be offered an opportunity to reinstall modified versions of the licensed software on the device and that there must not be any controls, such as firmware checking for checksums of the software on the device and consequent non-operation of the software or device due to the failure of such checks, unless the licensee/end user is given adequate information to bypass such controls.

This property only applies to:
1. Products normally used for personal, family, or household purposes (interpreted broadly).
2. Products designed or sold for incorporation into a dwelling.

**Known Instances:**
GPL-3.0, LGPL-3.0, AGPL-3.0.

---

#### Property: Nuclear Restriction
**Description:**
This property denies the use of the software in a nuclear facility. A mere warranty clause that does not deny use in a nuclear facility is not considered a restriction under this property.

---

#### Property: Patent Clause
**Description:**
This property indicates that the license has patent licensing-related terms. All patent-related provisions in a license, with the exception of a basic patent license, trigger this clause.

**Example:**
The Apache-2.0 license includes a license cancellation clause due to patent disputes.

---

#### Property: Distribute Source Code
**Description:**
This property indicates that the license requires that the source code of the OSS is either distributed or offered to distribute in connection with the software delivery.

---

#### Property: Modification-Related Obligations
**Description:**
This property indicates that the license contains obligations triggered by modifying the licensed content. The scope of obligations could vary, but typically it is about ensuring that:
- Recipients of the modified content don't attribute the modifications to the wrong author.
- The unmodified content is available to the recipients.

The obligations go beyond merely marking the modifications.

**Examples:**
Artistic-type licenses have this property, but also some others.

---

#### Property: AutoConf or Other Exception
**Description:**
This property indicates that the license includes an AutoConf exception or another type of exception to the license terms.

**Types of Exceptions:**
- Some exceptions render the license, assuming the exception criteria apply, permissive-style.
- Other exceptions do not render the license permissive-style but rather relax the terms of the license in other ways (e.g., introducing a list of compatible copyleft licenses).


---

## Policy Rules
### License Category Based Rules

#### Copyleft - Strong

**If product label is SaaS:** Allowed without violation.

**If product label is distributable:** Violation created for manual review, unless there is an acceptable established software interaction or applicable exclusion.

##### How to Fix

A copyleft license with a wide or harder-to-control scope of copyleft effect. The license requires software interacting with the licensed software to some wide extent to be licensed under the same copyleft license (copyleft effect). Further fact-finding by the project will be necessary to determine the extent of the copyleft effect in the present circumstances.

1. **First check for false positives.** The scanner could erroneously label the package or file with the wrong license.

2. **If the issue is not a false positive:**
   - Check whether the strong copyleft code is used without any linking, e.g., separate process or database, API, or RPC interaction.
   - If it is, create a resolution that clears the violation in ORT, using the resolution expression `LICENSE_ACQUIRED` in the project's `.yml` file, with the comment: *"Good architecture, and thus compliant."*

3. **If the issue is not solved with an architecture check, the alternatives are:**
   - (i) Change the architecture to be compliant (see above), or
   - (ii) Contact the Open Source Officer (OSO).

   If this is not possible, the component needs to be switched out, or another license or permission needs to be acquired.

##### How to Fix (by OSO)

1. **If the issue is not solved with an architecture check:**
   - (i) Relicense under the copyleft license the code covered by the copyleft effect.
   - (ii) Reanalyze dynamic linking options with legal/Double Open, etc.

   If this is not possible, the component needs to be switched out or another license or permission needs to be acquired.

2. **Any deviations, if approved, need to be recorded to ORT** with a resolution with the reason `CANT_FIX_ISSUE` in the project's `.ort.yml` file with the comment: *"Not Fixed, will be fixed ASAP."*

3. **If this requires a change by a third party that is not responsive,** consider creating a resolution with the reason `CANT_FIX_ISSUE` in the project's `.yml` file (if allowed as per project policy) with the comment: *"Not Fixed, will be fixed ASAP."*

#### Copyleft - LGPL

**If product label is SaaS:** Allowed without violation.

**If product label is distributable:** Allowed without violation if found as an open source dependency that is not built into own application. If this cannot be determined automatically or if found as a part or own application, must be manually reviewed.

##### How to Fix

A LGPL copyleft license requires code statically linking the same copyleft code, or being part of the same resulting binary, to follow the LGPL terms.

1. **First check for false positives.** The scanner could erroneously label the package or file with the wrong license.

2. **If the issue is not a false positive:**
   - Check whether it is a separate dependency which was not automatically detected.
   - If it is, create a resolution that clears the violation in ORT, using the resolution expression `LICENSE_ACQUIRED` in the project's `.yml` file, with the comment: *"separate open source dependency, and thus compliant."*

3. **Check if your own or third party proprietary code is part of the same binary as LGPL code:**
   - If it is not, the use is acceptable as such.
   - If it is, alternatives are:
     - (i) Change the interaction so that the own proprietary code no longer ends up in the same binary.
     - (ii) Contact the Open Source Officer (OSO) for other alternatives.

4. **If this is not possible,** the component needs to be switched out or another license needs to be acquired.

##### How to Fix (by OSO)

1. **If the issue is not solved with an architecture check:**
   - (i) Relicense under the copyleft license the code covered by the copyleft effect.
   - (ii) Create for users an opportunity to modify the LGPL licensed code and relink statically with the proprietary code.

2. **If this is not possible,** the component needs to be switched out or another license or permission needs to be acquired.

3. **Any deviations, if approved, need to be recorded to ORT** with a resolution with the reason `CANT_FIX_ISSUE` in the project's `.ort.yml` file with the comment: *"Not Fixed, will be fixed ASAP."*

4. **If this requires a change by a third party that is not responsive,** consider creating a resolution with the reason `CANT_FIX_ISSUE` in the project's `.yml` file (if allowed as per project policy) with the comment: *"Not Fixed, will be fixed ASAP."*

#### Copyleft - Module Level

**If product label is SaaS:** Allowed without violation.

**If product label is distributable:** Allowed without violation if found in an open source dependency. If found as a part of own application, must be manually reviewed.

##### How to Fix

A module level copyleft license requires code in the same module to be licensed under the same copyleft terms, for example Eclipse Public License (EPL-1.0).

1. **First check for false positives.** The scanner could erroneously label the package or file with the wrong license.

2. **If the issue is not a false positive:**
   - Check whether it is an open source dependency which was not automatically detected.
   - If it is, create a resolution that clears the violation in ORT, using the resolution expression `LICENSE_ACQUIRED` in the project's `.yml` file, with the comment: *"indirect dependency, and thus compliant."*

3. **Investigate if the copyleft code is in the same module as your own proprietary code:**
   - If it is not, the use case is acceptable as such.
   - If it is in the same module, alternatives are to:
     - (i) Change the interaction so that the own proprietary code no longer ends up in the same module.
     - (ii) Contact the Open Source Officer (OSO) for other alternatives.

4. **If this is not possible,** the component needs to be switched out or another license needs to be acquired.

##### How to Fix (by OSO)

1. **If the issue is not solved with an architecture check:**
   - Relicense under the copyleft license the code covered by the copyleft effect.

2. **Any deviations, if approved, need to be recorded to ORT** with a resolution with the reason `CANT_FIX_ISSUE` in the project's `.ort.yml` file with the comment: *"Not Fixed, will be fixed ASAP."*

3. **If this requires a change by a third party that is not responsive,** consider creating a resolution with the reason `CANT_FIX_ISSUE` in the project's `.yml` file (if allowed as per project policy) with the comment: *"Not Fixed, will be fixed ASAP."*

#### Copyleft - File-Level

**If product label is SaaS:** Allowed without violation.

**If product label is distributable:** Allowed without violation if found in a dependency. If found as a part or own application, must be manually reviewed.

##### How to Fix

If the file has a file level copyleft license, such as Mozilla Public License (MPL-2.0) and an own copyright notice:

1. **First check for false positives.** The scanner could erroneously label the package or file with the wrong license.

2. **If the issue is not a false positive:**
   - Check whether it is an open source dependency which was not automatically detected.
   - If it is, create a resolution that clears the violation in ORT, using the resolution expression `LICENSE_ACQUIRED` in the project's `.yml` file, with the comment: *"indirect dependency, and thus compliant."*

3. **Investigate if the copyleft code is in the same file as your own proprietary code:**
   - If it is not, the use case is acceptable as such.
   - If it is in the same file, alternatives are to:
     - (i) Change the interaction so that the own proprietary code no longer ends up in the same file.
     - (ii) Contact the Open Source Officer (OSO) for other alternatives.

4. **If this is not possible,** the component needs to be switched out or another license needs to be acquired.

##### How to Fix (by OSO)

1. **If the issue is not solved with an architecture check:**
   - Relicense under the copyleft license the code covered by the copyleft effect.

2. **Any deviations, if approved, need to be recorded to ORT** with a resolution with the reason `CANT_FIX_ISSUE` in the project's `.ort.yml` file with the comment: *"Not Fixed, will be fixed ASAP."*

3. **If this requires a change by a third party that is not responsive,** consider creating a resolution with the reason `CANT_FIX_ISSUE` in the project's `.yml` file (if allowed as per project policy) with the comment: *"Not Fixed, will be fixed ASAP."*

#### Permissive

**Allowed without violation.**

#### Free Restricted

**Allowed only by case-specific exceptions.**

##### How to Fix

The license contains restrictions regarding the usage of the software making it not open source in a strict sense.

1. **First check for false positives.** The scanner could erroneously label the package or file with the wrong license.

2. **Investigate whether those restrictions are compatible with the objectives and practices of the project:**
   - If the license is found to be acceptable, add a resolution to ORT using the resolution expression `LICENSE_ACQUIRED` in the project's `.yml` file, with the comment: *"free restricted license complied with"* or another justification.
   - If not possible, the component needs to be switched out or another license needs to be acquired.

3. **If no options remain,** contact the Open Source Officer (OSO) for additional steps.

##### How to Fix (by OSO)

1. **Any deviations, if approved, need to be recorded to ORT** with a resolution with the reason `CANT_FIX_ISSUE` in the project's `.ort.yml` file with the comment: *"Not Fixed, will be fixed ASAP."*

2. **If this requires a change by a third party that is not responsive,** consider creating a resolution with the reason `CANT_FIX_ISSUE` in the project's `.yml` file (if allowed as per project policy) with the comment: *"Not Fixed, will be fixed ASAP."*

#### Commercial

**Allowed only by case-specific exceptions.**

##### How to Fix

This may be third-party proprietary software offered under a direct commercial license between supplier and customer. Further fact-finding by the project will be necessary to determine the code's license status and function, if any.

1. **First check for false positives.** The scanner could erroneously label the package or file with the wrong license.
2. **If it is not a false positive:**
   - Check whether you already have the license.
3. **If it is an unknown commercial license:**
   - Ask OSO/Double Open to investigate the license status.
4. **Consider acquiring a license:**
   - If a license is acquired, create an ORT resolution in the project's `.yml` file using the reason `LICENSE_ACQUIRED` with a relevant comment.
5. **If the issue remains after investigation:**
   - The component needs to be switched out.
6. **If no options remain:**
   - Contact the Open Source Officer (OSO) for additional steps.

##### How to Fix (by OSO)

1. **Any deviations, if approved, need to be recorded to ORT** with a resolution using the reason `CANT_FIX_ISSUE` in the project's `.ort.yml` file with the comment: *"Not Fixed, will be fixed ASAP."*
2. **If this requires a change by a third party that is not responsive,** consider creating a resolution with the reason `CANT_FIX_ISSUE` in the project's `.yml` file (if allowed as per project policy) with the comment: *"Not Fixed, will be fixed ASAP."*

#### Public Domain

**Allowed without violation.**

#### Source-available

**Allowed only by case-specific exceptions.**

##### How to Fix

This is typically proprietary software (or not open source) which may be released through a source code distribution model that includes arrangements where the source can be viewed, and in some cases modified, but without necessarily meeting the criteria to be called open-source.

1. **First check for false positives.** The scanner could erroneously label the package or file with the wrong license.
2. **If the issue is not a false positive:**
   - Investigate whether the licensing model is compatible with the project's objectives.
3. **If the license is acceptable:**
   - Add a resolution to ORT using `LICENSE_ACQUIRED` in the project's `.yml` file with the comment: *"license complied with"*.
4. **If incompatible:**
   - The component needs to be switched out or another license acquired.
5. **If no options remain:**
   - Contact the Open Source Officer (OSO) for additional steps.

##### How to Fix (by OSO)

1. **Any deviations, if approved, need to be recorded to ORT** with a resolution using the reason `CANT_FIX_ISSUE` in the project's `.ort.yml` file with the comment: *"Not Fixed, will be fixed ASAP."*
2. **If this requires a change by a third party that is not responsive,** consider creating a resolution with the reason `CANT_FIX_ISSUE` in the project's `.yml` file (if allowed as per project policy) with the comment: *"Not Fixed, will be fixed ASAP."*

#### Unstated

**Allowed only by case-specific exceptions.**

##### How to Fix

Third-party software that has a copyright notice, but no stated license. The absence of a license poses a risk that the copyright owner may assert license obligations at some future time.

1. **First check for false positives.** The scanner could erroneously label the package or file with the wrong license.
2. **If the license cannot be determined:**
   - Contact the copyright owner through OSO/Double Open/Validos to establish license obligations.
3. **If a license is found:**
   - Add license finding curation to ORT via package configuration file.
4. **If not resolved:**
   - The component needs to be switched out or a license acquired.
5. **If no options remain:**
   - Contact the Open Source Officer (OSO) for additional steps.

##### How to Fix (by OSO)

1. **Any deviations, if approved, need to be recorded to ORT** with a resolution using the reason `CANT_FIX_ISSUE` in the project's `.ort.yml` file with the comment: *"Not Fixed, will be fixed ASAP."*
2. **If this requires a change by a third party that is not responsive,** consider creating a resolution with the reason `CANT_FIX_ISSUE` in the project's `.yml` file (if allowed as per project policy) with the comment: *"Not Fixed, will be fixed ASAP."*

### License Property Based Rules

#### property:network-clause

**Allowed only by case-specific exceptions.**

##### How to Fix

1. **Check for false positives:**
   - Correct license findings via package configuration file curation
   - Use `orth` CLI to generate package config
   - Consider path exclusions or resolution.yml entries for irrelevant files/issues

2. **If not a false positive:**
   - Investigate compatibility with project objectives and downstream users
   - Switch component or acquire different license if incompatible

3. **If unresolved:**
   - Contact Open Source Officer (OSO)

##### How to Fix (by OSO)

1. **Record deviations in ORT** with resolution reason `CANT_FIX_ISSUE` in `.ort.yml` and comment: *"Not Fixed, will be fixed ASAP"*

#### property:antitivo-clause

**Allowed without violation.**

#### property:advertising-clause

**Allowed, but ORT hint created on each instance.**

##### How to Fix

1. **Check for false positives:**
   - Curate license findings via package config
   - Use `orth` CLI for configuration
   - Consider path exclusions or resolution.yml entries

2. **If valid finding:**
   - Discuss feature presentation limitations with product lead
   - Contact OSO for compliance strategies

3. **If compliant:**
   - Create resolution with `LICENSE_ACQUIRED`

4. **If incompatible:**
   - Switch component or acquire different license

##### How to Fix (by OSO)

1. **For multiple instances:**
   - Consider creating project-specific rules

2. **Record deviations** with `CANT_FIX_ISSUE` in `.ort.yml` and comment: *"Not Fixed, will be fixed ASAP"*

3. **For unresponsive third parties:**
   - Create `.yml` resolution with `CANT_FIX_ISSUE` if allowed

#### property:non-commercial

**Denied in every case.**

##### How to Fix

1. **For false positives:**
   - Add license curation via package config
   - Use `orth` CLI for configuration

2. **If valid license:**
   - Remove files immediately
   - Consider alternative licensing options

3. **If license acquired:**
   - Create `LICENSE_ACQUIRED` resolution

4. **If unresolved:**
   - Contact OSO

##### How to Fix (by OSO)

1. **Record deviations** with `CANT_FIX_ISSUE` in `.ort.yml` and comment: *"Not Fixed, will be fixed ASAP"*

2. **For third party issues:**
   - Create `.yml` resolution with `CANT_FIX_ISSUE` if allowed

#### property:Include-in-notice-file

**Allowed without violation.**

#### property:patent-clause

**Allowed without violation.**
*No active rules for this property.*

#### property:distribute-source-code

**Allowed without violation.**
*Helps fulfill code delivery obligations under certain licenses.*

#### property:nuclear-restriction

**Allowed only by case-specific exceptions.**

##### How to Fix

1. **Check for false positives**
2. **If valid restriction:**
   - Remove affected files immediately
3. **If unresolved:**
   - Contact OSO

##### How to Fix (by OSO)

1. **Record deviations** with `CANT_FIX_ISSUE` in `.ort.yml` and comment: *"Not Fixed, will be fixed ASAP"*

---

## Version History
- **19.3.2025** - Sample version created for example purposes.