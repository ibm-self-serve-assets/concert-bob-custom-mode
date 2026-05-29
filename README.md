# concert-bob-custom-mode

## Overview
This repository contains files required to create **ConcertDef-SBOM** custom mode in BoB which can be leveraged to generate Application SBOM for given vulnerability scan reports. In Concert, creating an application with relevant components is necessary to upload vulnerability scan reports. The mode also helps in uploading the generated Application SBOMs and avaiable vulnerability scan reports to IBM Concert.

## Enabling the ConcertDef-SBOM custom mode

Follow the below steps to enable the custom mode **ConcertDef-SBOM**
1. On the top right of the BoB IDE chat window, click on **Settings** (gear icon).
2. Click on **Modes**
3. Locate **Global Modes** and click on **Open** to open Global Modes Configuration file.
4. Copy the content of custom mode **ConcertDef-SBOM** from `custom_modes.yaml`file available in this repository.
5. Copy `rules-concertdef-sbom` directory in your global directory. 

**Linux/macOS**: `cp -R rules-concertdef-sbom ~/.bob/`

__Note__: 
Global directory location

Linux/macOS: `~/.bob/` 
Windows: `%USERPROFILE%\.bob\`



6. Configure Concert MCP server following the steps provided in the [concert-custom-mcp-server](https://github.com/ibm-self-serve-assets/concert-custom-mcp-server) repository. This provides tools for uploading various artifacts to configured IBM Concert environment. 
7. Restart the BoB IDE.

**Ensure following before you begin**:
1. Concert MCP server is running and tools are loaded in BoB IDE.
2. Custom mode **ConcertDef-SBOM** is available in Mode Selector drop down in the bottom of chat window.

## Using custom mode and Concert MCP server tools
Trivy reports of robot-shop sample application are provided for verification in the directory `robot-shop-scan-reports`. It consists of a source code scan report and few image scan reports.
1. Open `robot-shop-scan-reports` directory in BoB IDE.
2. Select **ConcertDef-SBOM** custom mode for interaction.
3. Use prompts similar to following:
   ### Application SBOM Generation 
   *Trivy scan reports of "robot-shop" application container images and code repository are available in this directory. Refer the details and generate ConcertDef SBOM for application robot-shop. Do not add any extra information in SBOM for environment, service or public access points. The code repository URL to be included is "https://github.com/instana/robot-shop"*

   **Note**: As having source code repository URL is mandatory in Application SBOM if uploading source-code scan report, the detail of the same needs to be provided.  
   ### Uploading Applciation SBOM
   *Upload robot-shop ConcertDef SBOM  @/robot-shop-sbom.json to IBM Concert.*

   **Note**: Here `robot-shop-sbom.json` is the name of the ConcertDef SBOM generated in previous step.
   ### Uploading Vulnerability Scan Reports - Source Code
   *Upload source code scan report @/rs-repo-scan.json to robot-shop application in IBM Concert. The repository URL is https://github.com/instana/robot-shop*
   ### Uploading Vulnerability Scan Reports - Container Image
   *Upload Trivy Vulnerability Scan Reports of all images in this directory to IBM Concert*
   
