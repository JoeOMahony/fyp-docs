# Project Proposal

**Project Name:** Aeroq  
**Project Title:** Web application for early prediction of flight departure delays at Irish airports using decision trees 

*Submitted: 2026-09-17 15:59* 

## Project Overview

Irish airport departure boards only show delays once they're officially announced, but early indicators are often present in public data. I propose to build a system, Aeroq, which will take as input a user-provided flight number, fetch the relevant historical and live data, compute one or more probability indicators for the chance of a 15 minute delay or greater, and output, in a human-readable way, this indicator and some associated ‘reasoning’ information.

For example, an input of “EI 552” would return an expanded visual representation of: “85% chance of delay due to the aircraft running 25 minutes late on its inbound flight and strong crosswinds forecasted on approach.” The probability indicator would be computed along various time frames (6 h, 3 h, 1 h, 15 min) and the user given an option to subscribe to updates.

I would like to build this as I have always had a great interest in aviation, and am also interested in learning more about data systems. While flight delay prediction is well researched with U.S. data, services that predict delays early, like Flighty, rely on a proprietary black-box system behind a subscription.

I envisage this project will require a well-researched data architecture, elements of distributed computing for batch processing of weather observations (METARs/TAFs API) and aircraft data, and the implementation and continuous refinement of decision trees to arrive at probabilities, all tied together to serve users in a web app.

## Subject areas are related to this project idea

- Database & Analytics
- Information Systems & Modelling
- Software Development: Core
- Software Development: Front End
- Software Development: Back End

## Hardware and Software technologies I plan to use

Python, PostgreSQL, Express/React/Node.js, dec. trees, GitLab CI, S3/Lambda