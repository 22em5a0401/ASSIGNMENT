# ASSIGNMENT
FOR PROBLEM 1:
1. Product Overview
>The product is a vulnerability scanning tool for container images. It scans containers, identifies vulnerabilities (with severity levels), and presents this data in a way that helps users prioritize fixes.

2. Objectives
>Detect and list vulnerabilities in container images.
>Show severity levels (e.g., Critical, High, Medium, Low).
>Help users filter and prioritize which images to fix.
>Provide an intuitive UI to manage thousands of images efficiently.

3. Target Users
>DevOps teams
>Security engineers
>Infrastructure and operations teams

4. Key Features
>Image Scanning Dashboard
>Displays a summary of scanned container images.
>Highlights vulnerable images by severity.
>Image Details View

5. Functional Requirements
>Scheduled and manual scans.
>Store historical scan data.
>Role-based access control.


FOR PROBLEM 2:
1. Setup Local K8s Cluster
Minikube: Simple and widely used.
Kind (Kubernetes IN Docker): Lightweight and fast.
K3s: Minimal Kubernetes distribution.
MicroK8s: Good for Ubuntu-based systems.

3. Install a Kubernetes Security Scanner
Recommended Tool: Kubescape


curl -s https://raw.githubusercontent.com/kubescape/kubescape/master/install.sh | /bin/bash

Alternative Tools:
kube-bench (CIS Benchmark)
trivy k8s --report summary (Aqua Security)

3. Deliverable
A JSON file like results.json containing the findings.

📄 Sample JSON Output (Snippet)
json
Copy
Edit
{
  "framework": "NSA",
  "controlReports": [
    {
      "controlID": "C-001",
      "name": "Privileged containers",
      "status": "fail",
      "resources": ["pod/frontend"],
      "severity": "high"
    }
  ]
}


FOR PROBLEM 3:
TO CREATE A SIMPLE GOLANG WEBPAGE

// main.go
package main

import (
    "fmt"
    "net/http"
    "time"
)

func handler(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintf(w, "Current Date & Time: %s", time.Now().Format(time.RFC1123))
}

func main() {
    http.HandleFunc("/", handler)
    http.ListenAndServe(":8080", nil)
}


FOR DEPLOYMENT:

# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: datetime-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: datetime-app
  template:
    metadata:
      labels:
        app: datetime-app
    spec:
      containers:
      - name: datetime-container
        image: your-dockerhub-username/datetime-app
        ports:
        - containerPort: 8080

