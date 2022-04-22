# Architecture

Rough sketch... increase fidelity later

```mermaid
graph RL;
Portal
App1-->Portal
App2-->Portal
App3-->App2
CSS-->Portal
CSS-->App1
CSS-->App2
CSS-->App3
UI-->Portal
UI-->App1
UI-->App2
UI-->App3
```
