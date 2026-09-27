# Application of the Cross Industry Standard Process for Data Mining (CRISP-DM) to Aeroq

## Description

### Foreword

 CRISP-DM is a process model/framework for data mining projects. There are six primary phases and corresponding sub-phases.

 Six primary phases of the CRISP-DM:

 1. Business Understanding,
 2. Data Understanding,
 3. Data Preparation,
 4. Modeling,
 5. Evaluation,
 6. Deployment.


### Sources

- Wirth, R. and Hipp, J. (2000) CRISP-DM: Towards a Standard Process Model for Data Mining. Proceedings of the 4th International Conference on the Practical Applications of Knowledge Discovery and Data Mining, Manchester, 11-13 April 2000, 29-40.
- Chapman, P., Clinton, J., Kerber, R., Khabaza, T., Reinartz, T., Shearer, C. and Wirth, R., 2000. CRISP-DM 1.0: Step-by-step data mining guide. The CRISP-DM Consortium. Available at: https://mineracaodedados.wordpress.com/wp-content/uploads/2012/12/crisp-dm-1-0.pdf [Accessed 20 September 2026].
- Kelleher, J.D., Mac Namee, B. and D'Arcy, A. (2020) Fundamentals of machine learning for predictive data analytics: algorithms, worked examples, and case studies. 2nd ed. Cambridge, MA: MIT Press.

## 1. Business Understanding

### 1.1. Determine Business Objectives

#### 1.1.1 Background

**Project overview (from proposal)**

> Irish airport departure boards only show delays once they're officially announced, but early indicators are often present in public data. I propose to build a system, Aeroq, which will take as input a user-provided flight number, fetch the relevant historical and live data, compute one or more probability indicators for the chance of a 15 minute delay or greater, and output, in a human-readable way, this indicator and some associated ‘reasoning’ information. 
> 
> For example, an input of “EI 552” would return an expanded visual representation of: “85% chance of delay due to the aircraft running 25 minutes late on its inbound flight and strong crosswinds forecasted on approach.” The probability indicator would be computed along various time frames (6 h, 3 h, 1 h, 15 min) and the user given an option to subscribe to updates. I would like to build this as I have always had a great interest in aviation, and am also interested in learning more about data systems. While flight delay prediction is well researched with U.S. data, services that predict delays early, like Flighty, rely on a proprietary black-box system behind a subscription. I envisage this project will require a well-researched data architecture, elements of distributed computing for batch processing of weather observations (METARs/TAFs API) and aircraft data, and the implementation and continuous refinement of decision

#### 1.1.2 Business Objectives

#### 1.1.3 Business Success Criteria

Primary business objective

### 1.2. Assess Situation

#### 1.2.1 Inventory of Resources, Requirements, Assumptions, and Constraints

**Resources**

*People*

- Joe O'Mahony: Responsible for the entire project.
- Project supervisor: Allows meetings to provide guidance and feedback.

*Hardware, Software, and Cloud*

- AWS Lambda, a Function-as-a-Service (FaaS) offering by AWS used to ingest data on a regular basis.
- AWS S3, an object store offering by AWS used to store both structured and semi-structured data.

*Data*



**Requirements**

*Academic Requirements*

- Awaiting confirmation

**Assumptions**

- Due to the necessity of building a large corpus of data, only Dublin, Cork, and Shannon Airport will be considered by the system. In 2025, these three airports accounted for 97% of all passenger traffic in Ireland (https://www.cso.ie/en/releasesandpublications/ep/p-as/aviationstatisticsquarter4andyear2025/).
 
**Constraints**

- The schedule for submission dates must be met. TBC.

#### 1.2.2 Risks and Contingencies

#### 1.2.3 Terminology

#### 1.2.4 Costs and Benefits

### 1.3. Determine Data Mining Goals

#### 1.3.1 Data Mining Goals

#### 1.3.2 Data Mining Success Criteria

### 1.4. Produce Project Plan

#### 1.4.1 Project Plan

#### 1.4.2 Initial Assessment of Tools and Techniques

## 2. Data Understanding

## 3. Data Preparation

## 4. Modeling

## 5. Evaluation

## 6. Deployment