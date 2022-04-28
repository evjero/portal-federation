# Architecture

## Phase 1

Limited remotes

```mermaid
graph TB;
	subgraph :3002;
		UI(UI)
		C(CSS)
	end
	subgraph :3000;
		P(Portal)
		Shell
		App1
		App2
	end
```

## Phase 2

Add remotes

```mermaid
graph TB;
	subgraph :3005;
		App2
	end
	subgraph :3004;
		App1
	end
	subgraph :3003;
		Shell
	end
	subgraph :3002;
		UI(UI)
		C(CSS)
	end
	subgraph :3001;
		L(Login)
		M[(Mongo)]
	end
	subgraph :3000;
		P(Portal)
	end
```

## Phase 3

RD = Redux
MF = Module Federation

```mermaid
graph TD;
	subgraph Browser
		direction TB;
		U(-User-)
	end
	subgraph cluster1
		direction LR;
		subgraph Resources
			cfg(Configs)
		end
		subgraph podc1:3000;
			P(Portal)
			cfg-->P
		end
		subgraph podc1:3001;
			P--single-spa-->S(Shell)
			S-->Nav{Nav}
		end
		subgraph podc1:3002;
			App1
			Nav--router-->App1
		end
		subgraph podc1:3003;
			App2
			Nav--router-->App2
		end
		subgraph podc1:3004;
			App3
			Nav--router-->App3
		end
	end
	subgraph cluster2
		direction TB;
		subgraph podc2:3000;
			CSS([CSS])
			UI([UI])
		end
	end
	subgraph cluster3
		direction TB;
		subgraph podc3:3000;
			Login
		M[(Mongo)]
			U-->Login
			Login--OIDC-->P
		end
	end
```
