# Study Light

**Intent-Aware Predictive Lighting for a Dormitory Desk**

Hanyang University · Fall 2026 · CSE406 Software Engineering · Individual Project

Will the desk still be bright enough when I sit down to study? Study Light uses a planned start time and recent ambient light readings to answer that question. A browser-based 3D room shows the simulated lamp, and an activity log explains each automatic change.

In the dusk demonstration, the desk is still at 340 lx at 18:50. The controller forecasts 280 lx for a 19:00 study session, below its 300 lx target, and turns the lamp on at 10%. With the same daylight and no study plan, the lamp stays off. These results come from simulated readings.

## Project materials

| Resource | Purpose |
| --- | --- |
| [Project paper (PDF)](paper/Study-Light-Jin-Ziyao-Paper.pdf) | Requirements, controller design, and results for five functional checks |
| [Downloadable app](app/Study-Light.html) | Download and open this HTML file in a browser to run the simulation offline. |
| [WebM demonstration](demo/Study-Light-Demo.webm) | Watch the 52-second walkthrough. |
| [Development and verification](docs/development.md) | Follow the move from a study plan to a testable lighting decision. |

[Open Study Light in a browser](https://study-light-dorm-jzy26.shrewdblock1.chatgpt.site)

## System components

| Component | Responsibility |
| --- | --- |
| Study plan | Records whether the student plans to study and when the session starts. |
| Lighting controller | Forecasts daylight ten minutes before the session and adjusts lamp output every five minutes during study. A manual adjustment pauses the scenario. |
| Browser interface | Shows ambient light in lux, lamp output as a percentage, and the reason for each change. HTML and CSS provide the controls and layout. JavaScript runs the simulation, and WebGL renders the room. |

## Author

| Name | Contribution |
| --- | --- |
| Jin Ziyao · Department of Information Systems | Designed and implemented the prototype, verified the controller, and wrote the project paper. |
