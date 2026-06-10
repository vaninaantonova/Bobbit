# 04. IBM Systems Integration

**Integrating Quantum Computing with IBM Enterprise Platforms**

---

## Overview

This section provides practical guidance on integrating quantum computing with IBM's enterprise systems, including z/OS, IBM Cloud, and hybrid architectures.

---

## 1. IBM Quantum Platform Overview

### Core Components

**IBM Quantum Systems:**
- Physical quantum computers (50-1000+ qubits)
- Located in IBM data centers
- Accessed via cloud APIs
- Multiple system types (Eagle, Condor, Heron processors)

**Qiskit:**
- Open-source quantum SDK (Python)
- Circuit design and simulation
- Algorithm implementation
- Integration with classical systems

**Qiskit Runtime:**
- Optimized quantum-classical execution
- Reduced latency
- Session-based computing
- Serverless quantum functions

**IBM Quantum Network:**
- Enterprise access program
- Priority queue access
- Dedicated support
- Collaboration opportunities

---

## 2. Integration Architecture Patterns

### Pattern 1: Cloud-Native Quantum Integration

```
┌─────────────────────────────────────────────────┐
│           IBM Cloud (Orchestration)             │
│                                                 │
│  ┌──────────────┐      ┌──────────────┐       │
│  │  Classical   │      │   Quantum    │       │
│  │  Compute     │◄────►│   Service    │       │
│  │  (Python)    │      │  (Qiskit)    │       │
│  └──────────────┘      └──────────────┘       │
│         │                      │               │
│         ▼                      ▼               │
│  ┌──────────────┐      ┌──────────────┐       │
│  │  Data Store  │      │ IBM Quantum  │       │
│  │  (Cloud DB)  │      │   Hardware   │       │
│  └──────────────┘      └──────────────┘       │
└─────────────────────────────────────────────────┘
```

**Use Cases:**
- Cloud-native applications
- Microservices architecture
- API-first design
- Scalable quantum workloads

**Benefits:**
- Fast deployment
- Elastic scaling
- Pay-per-use pricing
- Modern DevOps practices

**IBM Services:**
- IBM Cloud Functions (serverless)
- IBM Cloud Kubernetes Service
- IBM Cloud Object Storage
- IBM Quantum Platform API

---

### Pattern 2: Hybrid z/OS Integration

```
┌─────────────────────────────────────────────────┐
│              On-Premises z/OS                   │
│                                                 │
│  ┌──────────────┐      ┌──────────────┐       │
│  │  Core        │      │  Batch Job   │       │
│  │  Transaction │      │  Scheduler   │       │
│  │  System      │      │  (JCL)       │       │
│  └──────────────┘      └──────┬───────┘       │
│                               │                │
└───────────────────────────────┼────────────────┘
                                │
                    ┌───────────▼───────────┐
                    │   IBM Cloud Connect   │
                    │   (Secure Gateway)    │
                    └───────────┬───────────┘
                                │
┌───────────────────────────────▼────────────────┐
│              IBM Cloud                          │
│                                                 │
│  ┌──────────────┐      ┌──────────────┐       │
│  │  Quantum     │      │  Results     │       │
│  │  Service     │─────►│  Processing  │       │
│  │  (Qiskit)    │      │  & Storage   │       │
│  └──────────────┘      └──────┬───────┘       │
│                               │                │
└───────────────────────────────┼────────────────┘
                                │
                    ┌───────────▼───────────┐
                    │   Return Results to   │
                    │   z/OS (API/MQ)       │
                    └───────────────────────┘
```

**Use Cases:**
- Mainframe batch optimization
- Risk analysis for banking
- Portfolio optimization
- Supply chain planning
- Fraud detection (batch)

**Benefits:**
- Leverage existing z/OS investments
- Secure data handling
- Proven reliability
- Gradual modernization

**IBM Services:**
- IBM Cloud Secure Gateway
- IBM MQ (messaging)
- z/OS Connect (REST APIs)
- IBM Cloud Private

**Implementation Steps:**
1. **Identify workload:** Select batch job for quantum acceleration
2. **Extract data:** Export from z/OS to cloud-compatible format
3. **Process quantum:** Run quantum algorithm via Qiskit Runtime
4. **Return results:** Import back to z/OS via secure channel
5. **Integrate:** Update z/OS application with quantum results

---

### Pattern 3: Hybrid Multi-Cloud

```
┌─────────────────────────────────────────────────┐
│         Enterprise Data Center                  │
│                                                 │
│  ┌──────────────┐      ┌──────────────┐       │
│  │  Legacy      │      │  Private     │       │
│  │  Systems     │      │  Cloud       │       │
│  └──────┬───────┘      └──────┬───────┘       │
│         │                     │                │
└─────────┼─────────────────────┼────────────────┘
          │                     │
          └──────────┬──────────┘
                     │
          ┌──────────▼──────────┐
          │   API Gateway       │
          │   (Integration)     │
          └──────────┬──────────┘
                     │
┌────────────────────┼────────────────────────────┐
│              IBM Cloud                          │
│                                                 │
│  ┌──────────────┐      ┌──────────────┐       │
│  │  Quantum     │      │  Classical   │       │
│  │  Workloads   │◄────►│  Workloads   │       │
│  └──────────────┘      └──────────────┘       │
│         │                      │               │
│         ▼                      ▼               │
│  ┌──────────────┐      ┌──────────────┐       │
│  │ IBM Quantum  │      │  Analytics   │       │
│  │  Platform    │      │  Services    │       │
│  └──────────────┘      └──────────────┘       │
└─────────────────────────────────────────────────┘
```

**Use Cases:**
- Complex enterprise architectures
- Multi-vendor environments
- Gradual cloud migration
- Distributed workloads

**Benefits:**
- Flexibility
- Risk mitigation
- Incremental adoption
- Best-of-breed approach

---

## 3. Qiskit Integration Guide

### 3.1 Basic Qiskit Setup

**Installation:**
```python
# Install Qiskit and IBM Quantum provider
pip install qiskit qiskit-ibm-runtime

# For optimization problems
pip install qiskit-optimization

# For machine learning
pip install qiskit-machine-learning

# For chemistry/nature
pip install qiskit-nature
```

**Authentication:**
```python
from qiskit_ibm_runtime import QiskitRuntimeService

# Save credentials (one-time)
QiskitRuntimeService.save_account(
    channel='ibm_quantum',
    token='YOUR_IBM_QUANTUM_TOKEN',
    overwrite=True
)

# Load service
service = QiskitRuntimeService()

# List available backends
backends = service.backends()
for backend in backends:
    print(f"{backend.name}: {backend.num_qubits} qubits")
```

---

### 3.2 Simple Quantum Circuit Example

```python
from qiskit import QuantumCircuit
from qiskit_ibm_runtime import QiskitRuntimeService, Sampler

# Create quantum circuit
qc = QuantumCircuit(2, 2)
qc.h(0)  # Hadamard gate on qubit 0
qc.cx(0, 1)  # CNOT gate
qc.measure([0, 1], [0, 1])  # Measure both qubits

# Connect to IBM Quantum
service = QiskitRuntimeService()
backend = service.least_busy(operational=True, simulator=False)

# Run on quantum hardware
sampler = Sampler(backend)
job = sampler.run(qc, shots=1000)
result = job.result()

print(f"Results: {result.quasi_dists}")
```

**TAM Note:** This creates an entangled state (Bell state) and measures it 1000 times. Use for demos and proof-of-concepts.

---

### 3.3 Optimization Example (QAOA)

```python
from qiskit_optimization import QuadraticProgram
from qiskit_optimization.algorithms import MinimumEigenOptimizer
from qiskit.algorithms.minimum_eigensolvers import QAOA
from qiskit.algorithms.optimizers import COBYLA
from qiskit.primitives import Sampler

# Define optimization problem
qp = QuadraticProgram()
qp.binary_var('x')
qp.binary_var('y')
qp.binary_var('z')

# Objective: minimize -x - 2y - 3z
qp.minimize(linear={'x': -1, 'y': -2, 'z': -3})

# Constraint: x + y + z <= 2
qp.linear_constraint({'x': 1, 'y': 1, 'z': 1}, '<=', 2)

# Solve with QAOA
qaoa = QAOA(sampler=Sampler(), optimizer=COBYLA(), reps=2)
optimizer = MinimumEigenOptimizer(qaoa)
result = optimizer.solve(qp)

print(f"Optimal solution: {result.x}")
print(f"Optimal value: {result.fval}")
```

**TAM Note:** This solves a simple portfolio selection problem. Scale up for real enterprise use cases.

---

### 3.4 Qiskit Runtime (Optimized Execution)

```python
from qiskit_ibm_runtime import QiskitRuntimeService, Session, Sampler
from qiskit import QuantumCircuit

# Create circuit
qc = QuantumCircuit(2)
qc.h(0)
qc.cx(0, 1)
qc.measure_all()

# Use session for multiple jobs
service = QiskitRuntimeService()
backend = service.backend("ibm_brisbane")

with Session(service=service, backend=backend) as session:
    sampler = Sampler(session=session)
    
    # Run multiple circuits efficiently
    job1 = sampler.run(qc, shots=1000)
    job2 = sampler.run(qc, shots=5000)
    
    result1 = job1.result()
    result2 = job2.result()
    
print("Session complete")
```

**Benefits:**
- Reduced queue time
- Lower latency
- Batch processing
- Cost optimization

**TAM Note:** Use sessions for production workloads to minimize overhead and cost.

---

## 4. z/OS Integration Patterns

### 4.1 Batch Job Integration

**Scenario:** Overnight portfolio optimization on z/OS

**Architecture:**
```
z/OS Batch Job (JCL)
    ↓
Extract portfolio data (COBOL/DB2)
    ↓
Export to CSV/JSON
    ↓
Transfer to IBM Cloud (SFTP/API)
    ↓
IBM Cloud Function (Python)
    ↓
Qiskit Runtime (QAOA optimization)
    ↓
Results back to z/OS (MQ/API)
    ↓
Update z/OS database (DB2)
    ↓
Generate reports (COBOL)
```

**Sample JCL:**
```jcl
//QUANTOPT JOB (ACCT),'QUANTUM OPT',CLASS=A,MSGCLASS=X
//STEP1    EXEC PGM=EXTRACT
//INPUT    DD DSN=PORTFOLIO.DATA,DISP=SHR
//OUTPUT   DD DSN=PORTFOLIO.JSON,DISP=(NEW,CATLG)
//STEP2    EXEC PGM=BPXBATCH
//STDOUT   DD SYSOUT=*
//STDERR   DD SYSOUT=*
//STDPARM  DD *
SH /usr/local/bin/quantum_submit.sh
/*
//STEP3    EXEC PGM=IMPORT
//INPUT    DD DSN=QUANTUM.RESULTS,DISP=SHR
//OUTPUT   DD DSN=PORTFOLIO.OPTIMIZED,DISP=(NEW,CATLG)
```

**Python Script (quantum_submit.sh calls):**
```python
import json
from qiskit_ibm_runtime import QiskitRuntimeService
from qiskit_optimization import QuadraticProgram

# Read portfolio data from z/OS
with open('/data/portfolio.json', 'r') as f:
    portfolio = json.load(f)

# Build optimization problem
qp = QuadraticProgram()
# ... (define problem based on portfolio data)

# Solve with quantum
service = QiskitRuntimeService()
# ... (run QAOA)

# Write results back
with open('/data/quantum_results.json', 'w') as f:
    json.dump(results, f)
```

---

### 4.2 z/OS Connect Integration

**Real-Time API Pattern:**

```
z/OS Application (CICS/IMS)
    ↓
z/OS Connect (REST API)
    ↓
IBM Cloud API Gateway
    ↓
Quantum Service (Qiskit Runtime)
    ↓
Response back through chain
```

**z/OS Connect Configuration:**
```json
{
  "serviceName": "QuantumOptimization",
  "serviceProvider": "REST",
  "baseURL": "https://api.quantum.ibm.com",
  "requestMapping": {
    "portfolioData": "$.input.portfolio",
    "constraints": "$.input.constraints"
  },
  "responseMapping": {
    "optimizedPortfolio": "$.output.solution",
    "confidence": "$.output.probability"
  }
}
```

**COBOL Program Calling Quantum Service:**
```cobol
IDENTIFICATION DIVISION.
PROGRAM-ID. QUANTCALL.

DATA DIVISION.
WORKING-STORAGE SECTION.
01  WS-REQUEST.
    05  WS-PORTFOLIO    PIC X(1000).
    05  WS-CONSTRAINTS  PIC X(500).
01  WS-RESPONSE.
    05  WS-SOLUTION     PIC X(1000).
    05  WS-CONFIDENCE   PIC 9(3)V99.

PROCEDURE DIVISION.
    CALL 'ZOSCONNECT' USING
        'QuantumOptimization'
        WS-REQUEST
        WS-RESPONSE.
    
    IF WS-CONFIDENCE > 95.00
        PERFORM PROCESS-SOLUTION
    ELSE
        PERFORM FALLBACK-CLASSICAL.
```

---

### 4.3 IBM MQ Integration

**Asynchronous Messaging Pattern:**

```
z/OS Application
    ↓
Put message to MQ Queue
    ↓
IBM Cloud MQ Bridge
    ↓
Cloud Function (triggered by MQ)
    ↓
Qiskit Runtime
    ↓
Put result to MQ Response Queue
    ↓
z/OS Application retrieves result
```

**Benefits:**
- Asynchronous processing
- Decoupled architecture
- Reliable message delivery
- Scalable

**MQ Message Format (JSON):**
```json
{
  "requestId": "REQ-2026-05-26-001",
  "problemType": "portfolio_optimization",
  "data": {
    "assets": [...],
    "constraints": {...},
    "riskTolerance": "medium"
  },
  "responseQueue": "QUANTUM.RESPONSE.QUEUE"
}
```

---

## 5. IBM Cloud Services Integration

### 5.1 IBM Cloud Functions (Serverless)

**Use Case:** On-demand quantum computations

```python
# IBM Cloud Function (Python)
def main(params):
    from qiskit_ibm_runtime import QiskitRuntimeService
    from qiskit_optimization import QuadraticProgram
    
    # Extract parameters
    problem_data = params.get('problem', {})
    
    # Build quantum problem
    qp = QuadraticProgram()
    # ... (build from problem_data)
    
    # Solve
    service = QiskitRuntimeService()
    # ... (run quantum algorithm)
    
    # Return results
    return {
        'solution': solution,
        'confidence': confidence,
        'executionTime': execution_time
    }
```

**Invocation:**
```bash
ibmcloud fn action invoke quantum-optimizer \
  --param problem '{"assets": [...], "constraints": {...}}' \
  --result
```

---

### 5.2 IBM Cloud Kubernetes Service

**Use Case:** Scalable quantum workload orchestration

**Deployment:**
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: quantum-service
spec:
  replicas: 3
  selector:
    matchLabels:
      app: quantum-service
  template:
    metadata:
      labels:
        app: quantum-service
    spec:
      containers:
      - name: quantum-worker
        image: ibmcloud/quantum-service:latest
        env:
        - name: QISKIT_IBM_TOKEN
          valueFrom:
            secretKeyRef:
              name: quantum-credentials
              key: token
        resources:
          requests:
            memory: "2Gi"
            cpu: "1"
          limits:
            memory: "4Gi"
            cpu: "2"
```

**Service:**
```yaml
apiVersion: v1
kind: Service
metadata:
  name: quantum-service
spec:
  selector:
    app: quantum-service
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080
  type: LoadBalancer
```

---

### 5.3 IBM Cloud Object Storage

**Use Case:** Store quantum results and intermediate data

```python
import ibm_boto3
from ibm_botocore.client import Config

# Configure COS client
cos = ibm_boto3.client(
    's3',
    ibm_api_key_id='YOUR_API_KEY',
    ibm_service_instance_id='YOUR_SERVICE_INSTANCE_ID',
    config=Config(signature_version='oauth'),
    endpoint_url='https://s3.us-south.cloud-object-storage.appdomain.cloud'
)

# Store quantum results
cos.put_object(
    Bucket='quantum-results',
    Key='optimization-2026-05-26.json',
    Body=json.dumps(quantum_results)
)

# Retrieve results
response = cos.get_object(
    Bucket='quantum-results',
    Key='optimization-2026-05-26.json'
)
results = json.loads(response['Body'].read())
```

---

## 6. Security & Compliance

### 6.1 Data Security

**Best Practices:**
- ✅ Encrypt data in transit (TLS 1.3)
- ✅ Encrypt data at rest (AES-256)
- ✅ Use IBM Cloud IAM for access control
- ✅ Implement least privilege principle
- ✅ Audit all quantum API calls
- ✅ Mask sensitive data before quantum processing

**Data Flow Security:**
```
z/OS (encrypted) → Secure Gateway → IBM Cloud (encrypted) → Quantum Platform
```

---

### 6.2 Compliance Considerations

**Regulatory Frameworks:**
- **GDPR:** Data residency, right to explanation
- **HIPAA:** PHI handling, audit trails
- **PCI DSS:** Cardholder data protection
- **SOC 2:** Security controls, availability

**IBM Quantum Compliance:**
- SOC 2 Type 2 certified
- ISO 27001 certified
- GDPR compliant
- Regular security audits

**TAM Guidance:**
"IBM Quantum Platform meets enterprise security standards. For highly sensitive data, consider data masking or synthetic data generation before quantum processing."

---

### 6.3 Access Control

**IBM Cloud IAM Roles:**
```
Viewer: Read-only access to quantum resources
Operator: Run quantum jobs, view results
Editor: Create/modify quantum programs
Administrator: Full access, manage users
```

**Service ID for Automation:**
```bash
# Create service ID
ibmcloud iam service-id-create quantum-automation \
  --description "Service ID for quantum automation"

# Create API key
ibmcloud iam service-api-key-create quantum-key quantum-automation \
  --description "API key for quantum service"

# Assign role
ibmcloud iam service-policy-create quantum-automation \
  --roles Operator \
  --service-name quantum-computing
```

---

## 7. Monitoring & Observability

### 7.1 IBM Cloud Monitoring

**Key Metrics:**
- Quantum job queue time
- Quantum job execution time
- Success/failure rates
- QPU utilization
- Cost per job
- API response times

**Monitoring Setup:**
```python
from ibm_cloud_sdk_core.authenticators import IAMAuthenticator
from ibm_platform_services import UsageReportsV4

# Setup monitoring
authenticator = IAMAuthenticator('YOUR_API_KEY')
usage_reports = UsageReportsV4(authenticator=authenticator)

# Get quantum usage
response = usage_reports.get_account_usage(
    account_id='YOUR_ACCOUNT_ID',
    billingmonth='2026-05'
)

quantum_usage = [
    usage for usage in response.get_result()['resources']
    if 'quantum' in usage['resource_name'].lower()
]

print(f"Quantum QPU hours: {quantum_usage}")
```

---

### 7.2 Logging

**Structured Logging:**
```python
import logging
import json

# Configure logging
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s'
)
logger = logging.getLogger('quantum-service')

# Log quantum job
logger.info(json.dumps({
    'event': 'quantum_job_submitted',
    'job_id': job.job_id(),
    'backend': backend.name,
    'circuit_depth': circuit.depth(),
    'num_qubits': circuit.num_qubits,
    'shots': 1000,
    'timestamp': datetime.now().isoformat()
}))
```

---

### 7.3 Alerting

**Alert Conditions:**
- Job failure rate > 10%
- Queue time > 1 hour
- Cost exceeds budget threshold
- API errors > 5% of requests
- Backend unavailability

**IBM Cloud Alerts:**
```yaml
alerts:
  - name: quantum-job-failures
    condition: failure_rate > 0.10
    notification: email, slack
    severity: high
  
  - name: quantum-cost-threshold
    condition: monthly_cost > $10000
    notification: email
    severity: critical
```

---

## 8. Cost Optimization

### 8.1 Cost Model

**IBM Quantum Pricing (Typical):**
- **Free Tier:** 10 minutes QPU time/month
- **Pay-as-you-go:** $1.60/second QPU time
- **Reserved:** Discounted rates for committed usage
- **Enterprise:** Custom pricing, dedicated access

**Cost Calculation:**
```
Cost = (QPU seconds) × (Rate per second) + (Classical compute) + (Storage)

Example:
- 100 quantum jobs
- 10 seconds QPU time each
- Total: 1000 seconds = $1,600
```

---

### 8.2 Cost Optimization Strategies

**1. Use Simulators for Development:**
```python
from qiskit_aer import AerSimulator

# Use simulator for testing (free)
simulator = AerSimulator()
job = simulator.run(circuit, shots=1000)
result = job.result()

# Only use real hardware for production
```

**2. Optimize Circuit Depth:**
```python
from qiskit.transpiler import PassManager
from qiskit.transpiler.passes import Optimize1qGatesDecomposition

# Optimize circuit before execution
pm = PassManager([Optimize1qGatesDecomposition()])
optimized_circuit = pm.run(circuit)

# Reduced depth = lower cost
print(f"Original depth: {circuit.depth()}")
print(f"Optimized depth: {optimized_circuit.depth()}")
```

**3. Batch Jobs:**
```python
# Submit multiple circuits in one job (more efficient)
circuits = [circuit1, circuit2, circuit3]
job = sampler.run(circuits, shots=1000)
results = job.result()
```

**4. Use Sessions:**
```python
# Sessions reduce queue time and cost
with Session(service=service, backend=backend) as session:
    sampler = Sampler(session=session)
    # Multiple jobs in same session
```

**5. Right-Size Shots:**
```python
# Don't over-sample
# 1000 shots often sufficient for optimization
# 10,000+ shots for high-precision requirements
job = sampler.run(circuit, shots=1000)  # Not 100,000
```

---

## 9. Performance Optimization

### 9.1 Circuit Optimization

**Techniques:**
- Reduce circuit depth
- Minimize two-qubit gates
- Use native gates
- Transpile for target backend

```python
from qiskit import transpile

# Transpile for specific backend
backend = service.backend('ibm_brisbane')
optimized_circuit = transpile(
    circuit,
    backend=backend,
    optimization_level=3  # Maximum optimization
)

print(f"Gate count reduced: {circuit.count_ops()} → {optimized_circuit.count_ops()}")
```

---

### 9.2 Error Mitigation

**Techniques:**
- Zero-noise extrapolation
- Probabilistic error cancellation
- Measurement error mitigation

```python
from qiskit_ibm_runtime import Estimator, Options

# Configure error mitigation
options = Options()
options.resilience_level = 1  # Enable error mitigation
options.optimization_level = 3

estimator = Estimator(backend=backend, options=options)
job = estimator.run(circuit, observable)
result = job.result()
```

---

## 10. TAM Integration Checklist

### Pre-Integration Assessment
- [ ] Identify quantum-suitable workload
- [ ] Assess data sensitivity and compliance
- [ ] Evaluate network connectivity (on-prem to cloud)
- [ ] Determine integration pattern (batch, real-time, hybrid)
- [ ] Estimate QPU time and costs
- [ ] Plan security and access control

### Technical Setup
- [ ] Provision IBM Quantum access
- [ ] Set up IBM Cloud account
- [ ] Configure secure connectivity (VPN, Secure Gateway)
- [ ] Install Qiskit and dependencies
- [ ] Test authentication and API access
- [ ] Implement monitoring and logging

### Development
- [ ] Develop quantum algorithm
- [ ] Test on simulator
- [ ] Optimize circuit
- [ ] Implement error handling
- [ ] Create integration code (z/OS, cloud)
- [ ] Test end-to-end workflow

### Production Deployment
- [ ] Security review and approval
- [ ] Performance testing
- [ ] Cost validation
- [ ] Deploy to production
- [ ] Monitor and optimize
- [ ] Document and train team

---

## Next Steps

- **For assessment:** See [05. Assessment Framework](../05-assessment-framework/README.md)
- **For value translation:** See [06. Value Translation](../06-value-translation/README.md)
- **For examples:** See [07. Examples & Case Studies](../07-examples-case-studies/README.md)

---

**Remember:** Start small with pilots, prove value, then scale. Integration complexity varies by architecture—choose the pattern that fits your client's environment and maturity level.