# Lateral movement

By escaping the container, by discovering IAM key pairs or by connecting to other containers within the same hosting 
machine, attackers can move laterally, finding their way to the CI pipeline(s).

The escape technique depends on misconfigurations or vulnerabilities within for example, a k8s cluster, and can include 
leveraging shared volumes, libraries or namespaces between the host and the container, or it can involve taking 
advantage of overprivileged container rights. 

The container itself may host IAM key pairs which could allow the attacker to log directly into the cloud platform 
hosting the cloud systems. 
