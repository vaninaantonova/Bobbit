# 03. Quantum Algorithms & Enterprise Use Cases

**Practical Guide for Technical Account Managers**

---

## Overview

This section maps quantum algorithms to real-world enterprise problems, focusing on business value and implementation considerations rather than mathematical details.

---

## Algorithm Selection Framework

```
Enterprise Problem → Problem Type → Quantum Algorithm → IBM Solution

Problem Types:
1. Optimization → VQE, QAOA, Quantum Annealing
2. Simulation → Quantum Phase Estimation, VQE
3. Machine Learning → QML, QSVM, Quantum Neural Networks
4. Search/Pattern Recognition → Grover's Algorithm
5. Cryptography → Shor's Algorithm (threat), QKD (solution)
```

---

## 1. Optimization Algorithms

### 1.1 QAOA (Quantum Approximate Optimization Algorithm)

**What It Solves:**
Combinatorial optimization problems with discrete variables

**Enterprise Use Cases:**
- **Portfolio Optimization:** Select optimal mix of assets
- **Vehicle Routing:** Minimize delivery routes and costs
- **Job Scheduling:** Optimize task assignments and timelines
- **Network Design:** Optimize topology and resource allocation
- **Supply Chain:** Minimize costs while meeting constraints

**Business Value:**
- Reduce operational costs by 10-30%
- Faster time-to-solution (hours → minutes)
- Explore more solution space than classical methods
- Better solutions for complex constraints

**When to Use:**
✅ Discrete optimization (yes/no decisions)  
✅ Multiple constraints  
✅ Large solution space (>10^6 possibilities)  
✅ Near-optimal solutions acceptable  

**When NOT to Use:**
❌ Simple linear programming  
❌ Continuous optimization (use VQE instead)  
❌ Real-time requirements  
❌ Small problem sizes (<100 variables)  

**IBM Solution:**
- Qiskit Optimization module
- IBM Quantum Platform
- Qiskit Runtime (optimized execution)

**Example Problem:**
```
Portfolio Optimization:
- 50 assets to choose from
- Budget constraint: $10M
- Risk tolerance: Medium
- Goal: Maximize return

Classical: Test ~2^50 combinations (infeasible)
QAOA: Find near-optimal in minutes
```

**TAM Talking Points:**
"QAOA can explore exponentially more portfolio configurations than classical optimization, potentially finding better risk-adjusted returns while respecting all your constraints."

---

### 1.2 VQE (Variational Quantum Eigensolver)

**What It Solves:**
Finding minimum energy states (ground states) of quantum systems

**Enterprise Use Cases:**
- **Drug Discovery:** Molecular structure optimization
- **Materials Science:** Design new materials with specific properties
- **Chemical Engineering:** Catalyst design and optimization
- **Battery Technology:** Optimize battery chemistry
- **Protein Folding:** Understand protein structures

**Business Value:**
- Accelerate R&D cycles (years → months)
- Reduce experimental costs (simulation before synthesis)
- Discover novel materials/molecules
- Competitive advantage in innovation

**When to Use:**
✅ Molecular simulation  
✅ Quantum chemistry problems  
✅ Materials design  
✅ Energy minimization problems  

**When NOT to Use:**
❌ Classical chemistry (small molecules)  
❌ Purely empirical research  
❌ Non-quantum systems  

**IBM Solution:**
- Qiskit Nature module
- IBM Quantum Platform
- Collaboration with research institutions

**Example Problem:**
```
Drug Discovery:
- Simulate molecule with 20 atoms
- Find lowest energy configuration
- Predict binding affinity

Classical: Exponential complexity (2^60 states)
VQE: Polynomial complexity with quantum advantage
```

**TAM Talking Points:**
"VQE enables simulation of molecular interactions that are intractable classically, potentially accelerating your drug discovery pipeline and reducing failed experiments."

---

### 1.3 Quantum Annealing (D-Wave Style)

**What It Solves:**
Optimization by finding global minimum of energy landscape

**Enterprise Use Cases:**
- **Traffic Optimization:** City-wide traffic flow
- **Logistics:** Warehouse location and routing
- **Financial Modeling:** Risk optimization
- **Manufacturing:** Production scheduling
- **Telecommunications:** Network optimization

**Business Value:**
- Real-world optimization at scale
- Handle thousands of variables
- Fast time-to-solution
- Proven commercial applications

**When to Use:**
✅ Large-scale optimization (1000+ variables)  
✅ QUBO formulation possible  
✅ Approximate solutions acceptable  
✅ Batch processing acceptable  

**When NOT to Use:**
❌ Requires gate-based quantum computing  
❌ Need exact solutions  
❌ Problem doesn't map to QUBO  

**IBM Solution:**
- IBM Quantum (gate-based) for QAOA
- Partner with D-Wave for annealing-specific problems
- Hybrid classical-quantum approaches

**Note for TAMs:**
IBM focuses on gate-based quantum computing (more versatile), but be aware of quantum annealing for specific optimization use cases.

---

## 2. Simulation Algorithms

### 2.1 Quantum Phase Estimation (QPE)

**What It Solves:**
Estimating eigenvalues of quantum systems (energy levels)

**Enterprise Use Cases:**
- **Quantum Chemistry:** Precise molecular energy calculations
- **Materials Science:** Electronic structure calculations
- **Condensed Matter Physics:** Phase transitions
- **Quantum Sensing:** High-precision measurements

**Business Value:**
- Higher accuracy than classical methods
- Enables previously impossible simulations
- Reduces need for expensive experiments
- Accelerates materials discovery

**When to Use:**
✅ Need high precision  
✅ Quantum system simulation  
✅ Research and development  
✅ Long-term strategic projects  

**When NOT to Use:**
❌ Near-term applications (requires fault-tolerant quantum)  
❌ Classical systems  
❌ Low-precision requirements  

**Timeline:**
- Current (2026): Limited demonstrations
- 2028-2030: Early practical applications
- 2030+: Widespread use with error correction

**IBM Solution:**
- Qiskit algorithms library
- Research collaborations
- Roadmap for fault-tolerant quantum computing

---

### 2.2 Quantum Simulation (General)

**What It Solves:**
Simulating quantum systems using quantum computers

**Enterprise Use Cases:**
- **Pharmaceuticals:** Drug-protein interactions
- **Energy:** Solar cell efficiency optimization
- **Aerospace:** Material stress analysis
- **Electronics:** Semiconductor design
- **Climate Science:** Molecular dynamics

**Business Value:**
- Simulate systems impossible for classical computers
- Reduce R&D costs and time
- Enable breakthrough innovations
- Competitive advantage in research-intensive industries

**When to Use:**
✅ Quantum systems (molecules, materials)  
✅ Many-body problems  
✅ Strong correlation effects  
✅ Research-driven organizations  

**When NOT to Use:**
❌ Classical physics simulations  
❌ Simple molecular systems  
❌ Short-term ROI requirements  

**IBM Solution:**
- Qiskit Nature
- IBM Research partnerships
- Quantum Simulators (classical emulation for development)

**TAM Talking Points:**
"Quantum simulation is a natural fit for quantum computers—simulating quantum systems that are exponentially hard for classical computers. This is where we expect earliest quantum advantage."

---

## 3. Machine Learning Algorithms

### 3.1 Quantum Support Vector Machines (QSVM)

**What It Solves:**
Classification problems with quantum feature spaces

**Enterprise Use Cases:**
- **Fraud Detection:** Identify fraudulent transactions
- **Credit Scoring:** Assess creditworthiness
- **Medical Diagnosis:** Disease classification
- **Customer Segmentation:** Marketing optimization
- **Anomaly Detection:** Cybersecurity, manufacturing

**Business Value:**
- Improved classification accuracy
- Handle high-dimensional data
- Faster training for certain datasets
- Better feature representation

**When to Use:**
✅ High-dimensional data  
✅ Complex classification boundaries  
✅ Medium-sized datasets (1000-100,000 samples)  
✅ Accuracy is critical  

**When NOT to Use:**
❌ Simple linear classification  
❌ Very large datasets (>1M samples)  
❌ Real-time inference required  
❌ Interpretability is critical  

**Current Status (2026):**
- Research stage, early commercial pilots
- Hybrid classical-quantum approaches
- Limited quantum advantage demonstrated

**IBM Solution:**
- Qiskit Machine Learning module
- IBM Quantum Platform
- Integration with classical ML pipelines

**TAM Talking Points:**
"QSVM can potentially improve classification accuracy for complex, high-dimensional problems like fraud detection, though it's still in early stages of commercial deployment."

---

### 3.2 Quantum Neural Networks (QNN)

**What It Solves:**
Pattern recognition and prediction using quantum circuits

**Enterprise Use Cases:**
- **Time Series Forecasting:** Stock prices, demand prediction
- **Image Recognition:** Quality control, medical imaging
- **Natural Language Processing:** Sentiment analysis
- **Recommendation Systems:** Personalization
- **Predictive Maintenance:** Equipment failure prediction

**Business Value:**
- Potential for better generalization
- Reduced training data requirements
- Novel feature representations
- Competitive advantage in AI

**When to Use:**
✅ Research and experimentation  
✅ Novel AI approaches needed  
✅ Long-term AI strategy  
✅ Hybrid quantum-classical architectures  

**When NOT to Use:**
❌ Production AI systems (not mature yet)  
❌ Need proven, reliable solutions  
❌ Short-term projects  

**Current Status (2026):**
- Active research area
- Proof-of-concept demonstrations
- Not yet production-ready

**Timeline:**
- 2026-2028: Research and pilots
- 2028-2030: Early commercial applications
- 2030+: Potential widespread adoption

**IBM Solution:**
- Qiskit Machine Learning
- IBM Research collaborations
- Hybrid quantum-classical frameworks

---

### 3.3 Quantum Generative Models

**What It Solves:**
Generating new data samples (similar to GANs)

**Enterprise Use Cases:**
- **Financial Modeling:** Generate synthetic market scenarios
- **Drug Discovery:** Generate novel molecular structures
- **Materials Design:** Generate candidate materials
- **Synthetic Data:** Privacy-preserving data generation
- **Risk Analysis:** Monte Carlo simulations

**Business Value:**
- Generate more diverse scenarios
- Faster Monte Carlo simulations
- Privacy-preserving synthetic data
- Novel design exploration

**When to Use:**
✅ Need diverse scenario generation  
✅ Monte Carlo simulations  
✅ Privacy-sensitive data  
✅ Research applications  

**When NOT to Use:**
❌ Simple random sampling sufficient  
❌ Production requirements  
❌ Need interpretable models  

**Current Status (2026):**
- Research stage
- Promising early results
- Limited commercial applications

**IBM Solution:**
- Qiskit Machine Learning
- Research partnerships
- Quantum-enhanced Monte Carlo

---

## 4. Search & Pattern Recognition

### 4.1 Grover's Algorithm

**What It Solves:**
Unstructured search in O(√N) time vs O(N) classically

**Enterprise Use Cases:**
- **Database Search:** Unstructured data queries
- **Pattern Matching:** Security, bioinformatics
- **Cryptanalysis:** Security testing
- **Optimization:** Search-based optimization
- **SAT Solving:** Constraint satisfaction

**Business Value:**
- Quadratic speedup for search
- Faster pattern recognition
- Enhanced security testing
- Theoretical foundation for other algorithms

**When to Use:**
✅ Unstructured search problems  
✅ Large search spaces  
✅ Quadratic speedup is valuable  
✅ Research and development  

**When NOT to Use:**
❌ Structured data (use indexes)  
❌ Small search spaces  
❌ Real-time requirements  
❌ Near-term production needs  

**Current Status (2026):**
- Well-understood theoretically
- Limited practical advantage (overhead costs)
- Used as subroutine in other algorithms

**TAM Talking Points:**
"Grover's algorithm provides theoretical speedup for search, but practical advantage requires large-scale, fault-tolerant quantum computers. More relevant as a building block for other quantum algorithms."

---

## 5. Cryptography Algorithms

### 5.1 Shor's Algorithm (The Threat)

**What It Solves:**
Factoring large numbers in polynomial time

**Enterprise Impact:**
- **Breaks RSA encryption** (widely used)
- **Breaks ECC** (elliptic curve cryptography)
- **Threatens:** Banking, e-commerce, VPNs, digital signatures
- **Timeline:** 2030-2035 for practical attacks

**Business Value (Risk Mitigation):**
- Understand quantum threat timeline
- Plan migration to quantum-safe cryptography
- Protect long-term sensitive data
- Regulatory compliance (future requirements)

**TAM Talking Points:**
"Shor's algorithm will eventually break current encryption. We need to start migrating to quantum-safe cryptography now to protect data with long-term sensitivity (medical records, state secrets, financial data)."

**Action Items for Clients:**
1. **Inventory:** Identify systems using RSA/ECC
2. **Prioritize:** Classify data by sensitivity and lifetime
3. **Pilot:** Test quantum-safe algorithms
4. **Migrate:** Transition critical systems (2026-2030)
5. **Monitor:** Track quantum computing progress

**IBM Solution:**
- IBM Quantum Safe technology
- z/OS quantum-safe cryptography
- Migration tools and consulting

---

### 5.2 Quantum Key Distribution (QKD) (The Solution)

**What It Solves:**
Provably secure key exchange using quantum mechanics

**Enterprise Use Cases:**
- **Financial Services:** High-value transactions
- **Government:** Classified communications
- **Healthcare:** HIPAA-compliant data transfer
- **Critical Infrastructure:** Power grid, telecom
- **Defense:** Military communications

**Business Value:**
- Provable security (physics-based)
- Eavesdropping detection
- Future-proof security
- Regulatory compliance

**When to Use:**
✅ Extremely sensitive data  
✅ Long-term security requirements  
✅ Point-to-point communication  
✅ Budget for specialized hardware  

**When NOT to Use:**
❌ General-purpose encryption  
❌ Long-distance communication (>100km without repeaters)  
❌ Cost-sensitive applications  
❌ Mobile/wireless scenarios  

**Current Status (2026):**
- Commercial QKD systems available
- Limited to ~100km distance
- Higher cost than classical VPN
- Growing deployment in finance and government

**IBM Solution:**
- IBM Quantum Network
- Partnerships with QKD vendors
- Integration with IBM Cloud security

**TAM Talking Points:**
"QKD provides the highest level of security for point-to-point communication, ideal for high-value financial transactions or classified government communications. It's available today, unlike many quantum computing applications."

---

## 6. Algorithm Selection Decision Tree

```
START: What problem are you solving?

├─ Optimization Problem?
│  ├─ Discrete variables (yes/no decisions)?
│  │  └─ QAOA or Quantum Annealing
│  └─ Continuous variables (molecular structure)?
│     └─ VQE
│
├─ Simulation Problem?
│  ├─ Quantum system (molecules, materials)?
│  │  └─ VQE or Quantum Simulation
│  └─ Classical system?
│     └─ Use classical simulation
│
├─ Machine Learning Problem?
│  ├─ Classification?
│  │  └─ QSVM (experimental)
│  ├─ Pattern recognition?
│  │  └─ QNN (research stage)
│  └─ Generative modeling?
│     └─ Quantum Generative Models (research)
│
├─ Search Problem?
│  ├─ Unstructured search?
│  │  └─ Grover's (future)
│  └─ Structured search?
│     └─ Use classical database
│
└─ Security Problem?
   ├─ Need quantum-safe encryption?
   │  └─ Post-quantum cryptography
   └─ Need provably secure communication?
      └─ QKD
```

---

## 7. Maturity & Timeline Matrix

| Algorithm | Maturity (2026) | Production Ready | Quantum Advantage | Timeline |
|-----------|----------------|------------------|-------------------|----------|
| **QAOA** | Medium | Pilots | Limited | 2026-2028 |
| **VQE** | Medium | Research/Pilots | Specific cases | 2026-2030 |
| **Quantum Annealing** | High | Yes (D-Wave) | Proven | Now |
| **QPE** | Low | No | Future | 2030+ |
| **QSVM** | Low-Medium | Pilots | Unclear | 2028-2030 |
| **QNN** | Low | No | Research | 2030+ |
| **Grover's** | Low | No | Future | 2030+ |
| **Shor's** | Low | No (threat) | Future threat | 2030-2035 |
| **QKD** | High | Yes | Proven | Now |

---

## 8. ROI Estimation Framework

### Quick ROI Assessment

**High ROI Potential:**
- Optimization problems saving >$1M annually
- Drug discovery reducing R&D time by months
- Portfolio optimization improving returns by 1-2%
- Supply chain optimization reducing costs by 10-20%

**Medium ROI Potential:**
- Machine learning improving accuracy by 5-10%
- Simulation reducing experimental costs
- Risk modeling improving predictions

**Low ROI Potential (Currently):**
- General-purpose computing
- Simple optimization problems
- Real-time applications
- Small-scale problems

### ROI Calculation Template

```
Annual Benefit = (Cost Savings + Revenue Increase) - Quantum Costs

Cost Savings:
- Reduced computation time: $X
- Fewer experiments needed: $Y
- Better resource allocation: $Z

Revenue Increase:
- Better decisions: $A
- Faster time-to-market: $B
- Competitive advantage: $C

Quantum Costs:
- QPU time: $D
- Development: $E
- Integration: $F
- Training: $G

ROI = (Annual Benefit / Total Investment) × 100%
```

---

## 9. Industry-Specific Algorithm Mapping

### Financial Services
- **Portfolio Optimization:** QAOA, VQE
- **Risk Analysis:** Quantum Monte Carlo
- **Fraud Detection:** QSVM
- **Trading Strategies:** Quantum ML
- **Security:** QKD, Quantum-Safe Crypto

### Healthcare & Pharma
- **Drug Discovery:** VQE, Quantum Simulation
- **Protein Folding:** VQE
- **Medical Imaging:** QNN
- **Genomics:** Quantum Pattern Matching
- **Clinical Trials:** Quantum Optimization

### Manufacturing
- **Supply Chain:** QAOA, Quantum Annealing
- **Production Scheduling:** QAOA
- **Quality Control:** QSVM
- **Materials Design:** VQE
- **Predictive Maintenance:** QNN

### Energy & Utilities
- **Grid Optimization:** QAOA
- **Battery Design:** VQE
- **Solar Cell Optimization:** Quantum Simulation
- **Demand Forecasting:** QNN
- **Resource Allocation:** Quantum Annealing

### Telecommunications
- **Network Optimization:** QAOA
- **Routing:** Quantum Annealing
- **Security:** QKD
- **Traffic Prediction:** QNN
- **Resource Allocation:** QAOA

---

## 10. TAM Conversation Starters by Algorithm

### For QAOA (Optimization)
"Your supply chain optimization problem has millions of possible configurations. QAOA can explore exponentially more solutions than classical methods, potentially reducing costs by 15-20%."

### For VQE (Simulation)
"Simulating this molecule classically would take years. VQE on quantum hardware could reduce that to weeks, accelerating your drug discovery pipeline significantly."

### For QSVM (Machine Learning)
"For your fraud detection system, QSVM might improve accuracy by finding patterns in high-dimensional data that classical ML misses. It's experimental but worth piloting."

### For QKD (Security)
"Given your need for ultra-secure communication for high-value transactions, QKD provides provably secure key exchange that's available today, unlike many quantum computing applications."

### For Quantum-Safe Crypto
"Shor's algorithm will eventually break your current encryption. We should start planning migration to quantum-safe algorithms now to protect your long-term sensitive data."

---

## Next Steps

- **For IBM integration:** See [04. IBM Systems Integration](../04-ibm-systems-integration/README.md)
- **For assessment:** See [05. Assessment Framework](../05-assessment-framework/README.md)
- **For value translation:** See [06. Value Translation](../06-value-translation/README.md)

---

**Remember:** Focus on business value and practical applicability. Most clients care about ROI and time-to-solution, not algorithm details. Use technical depth only when needed for architecture discussions.