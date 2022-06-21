# Lateral movement

Lateral movement within a cloud environment is similar to lateral movement within a traditional infrastructure, 
aside from the presence of container escape operations. For the latter, instead of moving laterally to physically 
separate systems, the move is between a virtual system and the physical system hosting that virtual system, allowing 
additional privileges making future operations both possible and easier. 

For example, moving from a public-facing web server process running within a Kubernetes (k8s) cluster to the system 
which is hosting that k8s container. The escape technique used depends on misconfigurations 
or vulnerabilities within the k8s cluster, and can include leveraging shared volumes, libraries or namespaces 
between the host and the container, or it can involve taking advantage of overprivileged container rights. 

The container itself may host IAM key pairs which could allow the attacker to simply log directly into the cloud 
platform hosting the cloud systems. By escaping the container, discovering IAM key pairs or connecting to other 
containers within the same hosting machine, attackers can move laterally and discover new cloud infrastructure.

Through this process, attackers can find their way to the CI pipelines.