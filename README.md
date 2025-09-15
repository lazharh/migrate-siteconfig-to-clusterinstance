# migrate-siteconfig-to-clusterinstance

This will migrate an Red Hat ACM (Advanced Cluster Management for Kubernetes) hub cluster version 2.12 and above for uste SiteConfig CR (SiteConfig files) to ClusterInstance CR/files. The ACM cluster must have spoke (managed) clusters installed originally based on siteConfig CR.
It is based on this Article: https://access.redhat.com/articles/7124143

Please update variables according to you situation.

In this code we applied the playbook on a cluster that has 2 cluster apps : clusters has a 3 nodes spoke cluster and a SNO, and a second clusters2 gitops Apps which handles another SNO.
For example: since I have run this playbook on a hub cluster with 2 Apps , I have 2 variables related to this and also 2 variables related to git repo. Maybe you need more , or only one.



