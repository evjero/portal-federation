# Architecture

Rough sketch... increase fidelity later

RD = Redux
MF = Module Federation

```mermaid
graph TD;
	subgraph External
		direction TB;
		U(-User-)
	end
	subgraph Cluster 1;
		direction TB;
		U-->Portal(Portal)
		Main
		Portal--RD-->Main
		Main--router-->App1
		Main--router-->App2
		App2--router-->App3
	end
	subgraph Cluster 2
		direction TB;
		CSS([CSS])--MF-->Portal
		CSS--MF-->Main
		CSS--MF-->App1
		CSS--MF-->App2
		CSS--MF-->App3
		UI([UI])--MF-->Portal
		UI--MF-->Main
		UI--MF-->App1
		UI--MF-->App2
		UI--MF-->App3
	end


```
