# 02. Enterprise Mapping: Classical to Quantum

**Translating Enterprise Computing Paradigms to Quantum Equivalents**

---

## Overview

This section maps familiar enterprise computing concepts to their quantum counterparts, helping you explain quantum computing using terminology your clients already understand.

---

## 1. Computing Paradigm Mapping

### Sequential Processing → Quantum Circuit Execution

**Classical Sequential:**
```
Step 1 → Step 2 → Step 3 → Result
Each step depends on previous step
Time = O(n) for n steps
```

**Quantum Circuit:**
```
Initialize → Apply Gates → Measure
Gates applied in sequence, but operate on superposition
Time = O(log n) for many problems
```

**Enterprise Translation:**
"Like a pipeline that processes multiple scenarios simultaneously rather than one at a time."

---

### Parallel Processing → Quantum Superposition

**Classical Parallel:**
```
Task 1 → CPU 1
Task 2 → CPU 2
Task 3 → CPU 3
...
Task N → CPU N

Resources needed: N CPUs for N tasks
```

**Quantum Superposition:**
```
All N tasks encoded in quantum state
Single quantum system explores all paths
Resources needed: log₂(N) qubits

Example: 1000 tasks
- Classical: 1000 CPUs
- Quantum: 10 qubits (2^10 = 1024)
```

**Enterprise Translation:**
"Instead of scaling horizontally with more servers, quantum scales exponentially with more qubits."

**When to Use:**
- Optimization problems (scheduling, routing, portfolio)
- Combinatorial search spaces
- Configuration testing

---

### Distributed Computing → Quantum Entanglement

**Classical Distributed:**
```
Node A ←→ Network ←→ Node B
- Communication latency
- Bandwidth limitations
- Synchronization overhead
- Network failures
```

**Quantum Entanglement:**
```
Qubit A ←→ Entangled ←→ Qubit B
- Instantaneous correlation
- No bandwidth concept
- Perfect synchronization
- Fragile to decoherence
```

**Enterprise Translation:**
"Entanglement provides stronger correlations than any classical distributed system, enabling new cryptographic protocols and algorithm efficiencies."

**When to Use:**
- Quantum cryptography discussions (QKD)
- Quantum communication protocols
- Distributed quantum computing architectures

---

### Batch Processing → Quantum Annealing

**Classical Batch:**
```
Job Queue → Scheduler → Execution → Results
- Process jobs sequentially or in parallel
- Each job independent
- Predictable completion time
```

**Quantum Annealing:**
```
Problem → Encode in Hamiltonian → Anneal → Measure
- System evolves to lowest energy state
- Finds optimal or near-optimal solution
- Probabilistic completion time
```

**Enterprise Translation:**
"Like batch optimization where the system naturally settles into the best configuration, similar to how water finds the lowest point."

**When to Use:**
- Optimization problems (D-Wave systems)
- Scheduling and resource allocation
- Portfolio optimization
- Supply chain optimization

**IBM Solution:** IBM Quantum + Qiskit optimization modules

---

### Caching → Quantum Amplitude Amplification

**Classical Caching:**
```
Frequently accessed data → Cache (fast)
Rarely accessed data → Storage (slow)
Hit rate determines performance
```

**Quantum Amplitude Amplification:**
```
Correct answers → Amplified probability
Incorrect answers → Suppressed probability
Measurement yields correct answer with high probability
```

**Enterprise Translation:**
"Quantum algorithms amplify the 'signal' of correct answers while suppressing 'noise' of incorrect ones, similar to how caching prioritizes frequently needed data."

**When to Use:**
- Explaining Grover's search algorithm
- Database search optimization discussions
- Pattern recognition use cases

---

### Load Balancing → Quantum Interference

**Classical Load Balancing:**
```
Requests → Load Balancer → Distribute to servers
Goal: Even distribution, maximize throughput
```

**Quantum Interference:**
```
Quantum paths → Constructive/Destructive interference
Goal: Amplify correct paths, cancel incorrect paths
```

**Enterprise Translation:**
"Quantum interference is like intelligent load balancing where the system automatically routes 'traffic' toward optimal solutions and away from poor ones."

**When to Use:**
- Explaining quantum algorithm mechanics
- Discussing why quantum is probabilistic
- Technical architecture reviews

---

## 2. Data Structure Mapping

### Relational Database → Quantum State Vector

**Classical Database:**
```
Table with N rows
Each row: one record
Query: filter and retrieve specific rows
Storage: O(N) space
```

**Quantum State Vector:**
```
Superposition of N states
Each state: one possibility
Measurement: collapse to one state
Storage: O(log N) qubits
```

**Enterprise Translation:**
"A quantum state is like a database where all rows exist simultaneously until you query it, then you get one result based on probability."

---

### Key-Value Store → Quantum Register

**Classical Key-Value:**
```
Key → Value mapping
Direct access by key
O(1) lookup time
```

**Quantum Register:**
```
Qubit index → Quantum state
Superposition of all values
O(√N) search time (Grover's)
```

**Enterprise Translation:**
"Quantum registers can search unstructured data faster than classical key-value stores for certain query types."

---

### Graph Database → Quantum Walk

**Classical Graph:**
```
Nodes and edges
Traversal algorithms (BFS, DFS)
Time: O(V + E)
```

**Quantum Walk:**
```
Quantum superposition over graph
Explores multiple paths simultaneously
Time: O(√N) for certain problems
```

**Enterprise Translation:**
"Quantum walks explore network topologies exponentially faster, useful for social network analysis, fraud detection, and recommendation systems."

**When to Use:**
- Network optimization
- Fraud detection
- Recommendation engines
- Supply chain analysis

---

## 3. Security & Cryptography Mapping

### Encryption (RSA/ECC) → Quantum-Safe Cryptography

**Classical Encryption:**
```
Security based on factoring difficulty
RSA: Factor large numbers (hard classically)
ECC: Discrete logarithm (hard classically)
```

**Quantum Threat:**
```
Shor's algorithm: Factor in polynomial time
Breaks RSA, ECC in hours/days (future quantum computers)
```

**Quantum-Safe Solutions:**
```
Lattice-based cryptography
Hash-based signatures
Code-based cryptography
Post-quantum algorithms (NIST standards)
```

**Enterprise Translation:**
"Current encryption will be vulnerable to future quantum computers. We need to transition to quantum-safe algorithms now to protect long-term data."

**Timeline for TAMs:**
- **2026-2028:** Pilot quantum-safe implementations
- **2028-2030:** Migrate critical systems
- **2030+:** Full quantum-safe infrastructure

**IBM Solutions:**
- IBM Quantum Safe technology
- z/OS quantum-safe cryptography
- Cloud quantum-safe services

---

### VPN/Secure Communication → Quantum Key Distribution (QKD)

**Classical VPN:**
```
Shared secret key (vulnerable to interception)
Key exchange protocols (Diffie-Hellman)
Security based on computational difficulty
```

**Quantum Key Distribution:**
```
Keys encoded in quantum states
Eavesdropping detectable (measurement disturbs state)
Security based on physics, not computation
```

**Enterprise Translation:**
"QKD provides provably secure communication channels where any eavesdropping attempt is immediately detected, unlike classical encryption which can be recorded and decrypted later."

**When to Use:**
- Financial services (high-value transactions)
- Government/defense communications
- Healthcare (HIPAA compliance)
- Critical infrastructure

**Limitations to Mention:**
- Distance limited (currently ~100km without repeaters)
- Requires specialized hardware
- Higher cost than classical VPN

---

## 4. Workload Pattern Mapping

### OLTP (Online Transaction Processing) → Not Quantum-Suitable

**Classical OLTP:**
```
High-volume, low-latency transactions
ACID properties
Sequential consistency
```

**Quantum Reality:**
```
❌ Not suitable for OLTP
- Quantum operations are probabilistic
- Measurement destroys state
- Decoherence limits operation time
```

**TAM Guidance:**
"Keep OLTP workloads on classical systems (z/OS, cloud databases). Quantum is not a replacement for transactional systems."

---

### OLAP (Online Analytical Processing) → Quantum-Suitable (Specific Cases)

**Classical OLAP:**
```
Complex queries on large datasets
Aggregations, joins, analytics
Batch-oriented
```

**Quantum Opportunity:**
```
✅ Optimization queries (best configuration)
✅ Pattern recognition (anomaly detection)
✅ Simulation (what-if scenarios)
❌ Simple aggregations (SUM, AVG, COUNT)
```

**TAM Guidance:**
"Quantum can accelerate specific OLAP workloads like optimization and pattern recognition, but not general-purpose analytics."

---

### Batch Analytics → Quantum Optimization

**Classical Batch:**
```
Nightly ETL jobs
Report generation
Data warehouse updates
```

**Quantum Opportunity:**
```
✅ Portfolio optimization (overnight runs)
✅ Supply chain optimization (weekly planning)
✅ Risk analysis (Monte Carlo simulations)
✅ Molecular simulation (drug discovery)
```

**Enterprise Translation:**
"Replace overnight optimization jobs with quantum-accelerated solutions, reducing time from hours to minutes for complex problems."

**IBM Integration Pattern:**
```
z/OS Batch Job → IBM Cloud → Qiskit Runtime → Results back to z/OS
```

---

### Real-Time Processing → Not Quantum-Suitable (Yet)

**Classical Real-Time:**
```
Millisecond latency requirements
Streaming data processing
Immediate response needed
```

**Quantum Reality:**
```
❌ Not suitable for real-time (current technology)
- Quantum operations take microseconds to milliseconds
- Multiple measurements needed (shots)
- Queue time on shared quantum systems
```

**TAM Guidance:**
"Quantum is currently best for batch/near-real-time workloads. Real-time applications should remain on classical systems."

**Future Outlook:**
- 2028-2030: Near-real-time quantum (seconds)
- 2030+: Potential real-time quantum for specific use cases

---

## 5. Infrastructure Mapping

### On-Premises Data Center → IBM Quantum Cloud

**Classical On-Prem:**
```
Physical servers
Local control
Capital expense
Maintenance overhead
```

**Quantum Cloud:**
```
IBM Quantum systems (cloud-based)
API access via Qiskit
Pay-per-use (QPU time)
IBM maintains hardware
```

**Hybrid Pattern:**
```
On-Prem (z/OS, classical workloads)
    ↕
IBM Cloud (orchestration, preprocessing)
    ↕
IBM Quantum (quantum acceleration)
    ↕
Results back to on-prem
```

**Enterprise Translation:**
"Quantum computing is delivered as a cloud service, similar to how you might use cloud GPUs for AI workloads while keeping core systems on-premises."

---

### Mainframe (z/OS) → Quantum Integration

**z/OS Strengths:**
```
Transaction processing
Data integrity
Reliability (99.999% uptime)
Legacy application support
```

**Quantum Integration:**
```
z/OS → IBM Cloud → Quantum → z/OS
Use cases:
- Fraud detection (batch analysis)
- Portfolio optimization (overnight)
- Risk modeling (periodic)
- Supply chain optimization (weekly)
```

**TAM Talking Points:**
"Your z/OS systems remain the system of record. Quantum acts as a specialized accelerator for specific optimization and simulation workloads, accessed via APIs."

**IBM Solution:** IBM Quantum Network + z/OS integration patterns

---

### Microservices → Quantum Services

**Classical Microservices:**
```
Service A → Service B → Service C
REST APIs, message queues
Independently deployable
```

**Quantum Services Pattern:**
```
Classical Service → Quantum Service (API) → Classical Service
Quantum as a microservice
Qiskit Runtime as serverless function
```

**Enterprise Translation:**
"Integrate quantum computing as a microservice in your architecture, calling it via API when you need quantum acceleration for specific tasks."

**Example Architecture:**
```
Frontend → API Gateway → Orchestration Service
                              ↓
                         Quantum Service (Qiskit Runtime)
                              ↓
                         Results Processing → Database
```

---

## 6. Error Handling Mapping

### Classical Error Correction → Quantum Error Mitigation

**Classical Error Correction:**
```
Redundancy (RAID, replication)
Checksums and parity bits
Retry logic
Predictable error rates (10^-15 typical)
```

**Quantum Error Mitigation:**
```
Error mitigation techniques (not full correction)
Multiple measurements (shots)
Post-processing and filtering
Higher error rates (10^-3 to 10^-2 typical)
```

**Enterprise Translation:**
"Quantum systems require more sophisticated error handling than classical systems, similar to how wireless networks need error correction due to noisy channels."

**Current State (NISQ Era):**
- Error mitigation (reduce errors)
- Not full error correction (too expensive in qubits)

**Future State (Fault-Tolerant Era):**
- Full quantum error correction
- Logical qubits (1000+ physical qubits per logical qubit)
- Timeline: 2030+

---

### Retry Logic → Multiple Shots

**Classical Retry:**
```
Try operation
If fail → retry (up to N times)
Exponential backoff
```

**Quantum Shots:**
```
Run quantum circuit
Measure (get one result)
Repeat 1000-100,000 times
Analyze probability distribution
```

**Enterprise Translation:**
"Quantum algorithms are probabilistic, requiring multiple runs to build confidence in results, similar to Monte Carlo simulations."

**TAM Guidance on Shot Count:**
- Simple problems: 1,000-10,000 shots
- Complex problems: 10,000-100,000 shots
- Higher shots = higher confidence, but more cost/time

---

## 7. Performance Metrics Mapping

### Classical Metrics → Quantum Metrics

| Classical Metric | Quantum Equivalent | Typical Value |
|-----------------|-------------------|---------------|
| CPU Clock Speed | Gate Time | 10-100 ns |
| RAM Size | Number of Qubits | 50-1000 qubits (2026) |
| Disk IOPS | Circuit Depth | 100-1000 gates |
| Network Latency | Decoherence Time | 100 μs - 1 ms |
| Error Rate | Gate Fidelity | 99-99.9% |
| Throughput | Shots per Second | 1000-10,000 |

**Enterprise Translation:**
"Quantum performance is measured differently than classical systems. Focus on problem-specific metrics like solution quality and time-to-solution rather than traditional benchmarks."

---

## 8. Cost Model Mapping

### Classical TCO → Quantum Cost Model

**Classical TCO:**
```
Hardware (CapEx)
Software licenses
Maintenance
Power/cooling
Personnel
```

**Quantum Cost Model:**
```
QPU time (pay-per-use)
Classical preprocessing (cloud compute)
Development (Qiskit, algorithms)
Integration (APIs, orchestration)
Training (team upskilling)
```

**Pricing Example (IBM Quantum):**
- Development/testing: Free tier available
- Production: Pay per QPU second
- Enterprise: Reserved capacity options

**TAM Guidance:**
"Quantum is OpEx, not CapEx. Start with free tier for experimentation, scale to paid tiers for production workloads."

---

## 9. Quick Reference: Mapping Cheat Sheet

```
Classical → Quantum Mapping

COMPUTING:
Sequential → Circuit Execution
Parallel → Superposition
Distributed → Entanglement
Batch → Annealing

DATA:
Database → State Vector
Key-Value → Quantum Register
Graph → Quantum Walk

SECURITY:
RSA/ECC → Quantum-Safe Crypto
VPN → QKD

WORKLOADS:
OLTP → ❌ Not Suitable
OLAP → ✅ Specific Cases
Batch → ✅ Optimization
Real-Time → ❌ Not Yet

INFRASTRUCTURE:
On-Prem → Quantum Cloud
z/OS → Hybrid Integration
Microservices → Quantum Services

ERRORS:
Error Correction → Error Mitigation
Retry Logic → Multiple Shots
```

---

## 10. TAM Conversation Framework

### Step 1: Identify Client's Current Architecture
"Tell me about your current infrastructure and workload patterns."

### Step 2: Map to Quantum Equivalents
"Your batch optimization workload maps well to quantum annealing..."

### Step 3: Explain Using Enterprise Analogies
"Think of quantum superposition like parallel processing, but exponentially more efficient..."

### Step 4: Assess Fit
"Based on your workload characteristics, quantum could provide value for X, but not for Y..."

### Step 5: Propose Integration Pattern
"We'd integrate quantum as a cloud service, keeping your z/OS systems as the system of record..."

---

## Next Steps

- **For specific algorithms:** See [03. Algorithms & Use Cases](../03-algorithms-use-cases/README.md)
- **For IBM integration:** See [04. IBM Systems Integration](../04-ibm-systems-integration/README.md)
- **For client assessment:** See [05. Assessment Framework](../05-assessment-framework/README.md)

---

**Remember:** Always start with what the client knows (enterprise computing) and bridge to quantum concepts using familiar analogies. Avoid quantum physics unless specifically requested.