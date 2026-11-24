# Development and verification

Study Light is an individual software engineering project by Jin Ziyao. This retrospective describes the design decisions behind the submitted prototype.

## From a study plan to a lighting requirement

My earlier study planner asked when a student intended to work. For the dormitory lighting project I kept the study start time and added a question: will the desk still be bright enough at that time? A student can also turn off the plan for today. That setting lets me test whether a lighting action actually depends on the student's intent.

## Predicting light before the session

I used a synthetic light trace so the same daylight conditions could be replayed with different study plans. In the dusk scenario the room falls from 460 lx at 18:30 to 340 lx at 18:50. Continuing this trend for ten minutes predicts 280 lx at 19:00. With a study plan enabled, the controller compares that forecast with the 300 lx target and turns the virtual lamp on at 10%.

## Making the decision visible

The browser app presents a rotatable 3D desk, a manual switch, a brightness slider and an activity log. I revised the reading label to **Ambient light（当前环境光）** so that the sensor value in lux is distinguishable from lamp output in percent. During a running simulation, moving the slider hands control back to the student.

## Reproducing the checks

Download the [app](../app/Study-Light.html) and open it in a browser. Set the start time to 19:00. Begin each automatic check with the lamp off, select the stated light trend, and run the forecast.

| Case | Input or action | Expected observation |
| --- | --- | --- |
| Dusk and recovery | Study today enabled; select dusk and recovery | At 18:50 the lamp turns on at 10%. At 19:10 it reaches 75%, then dims to 25% at 19:15 and switches off at 19:20. |
| No plan | Disable Study today and replay the same dusk trace | The forecast still reaches 280 lx, but the lamp stays off. |
| Stable daylight | Enable Study today and select stable light | The lamp stays off when ambient light remains near 460 lx. |
| Manual override | Move the slider to 55% during the running dusk scenario | The clock stops and the lamp stays at the selected output. |

The [project paper](../paper/Study-Light-Jin-Ziyao-Paper.pdf) reports the results. The [demo](../demo/Study-Light-Demo.webm) shows the virtual lamp. The physical-device buttons require separately configured Apple Home shortcuts; physical lamp response was not measured.
