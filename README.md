# migrate-siteconfig-to-clusterinstance

DISCLAIMER: This is personal work and not supported by Red Hat.

0- Read these two articles before starting: https://access.redhat.com/articles/7124143 and https://access.redhat.com/articles/7105238

1 - Convert your clusters files from SiteConfig yamls to ClusterInstance using this tool: https://github.com/openshift-kni/cnf-features-deploy/tree/master/ztp/tools/siteconfig-converter#siteconfig-to-clusterinstance-converter

2- extraManifests section in siteConfig and crTemplates are ignored in the conversion and you will receive a warning about that. In my opinion you do not need those because the clusters are already created and Manifests are applied. but for both extraManifest and crTemplates: you can create a different ai-cluster-template-v2 from -v1 (this to be done beforehand). extraManifes
t requires also creating the configMap with all the manifest files referred to in that configMap (see article in 0-)

3 - Prepare the kustomization yaml file (name is kustomization.yaml-for-clusterInstance): the SiteConfig yaml file used to go to generators Section, but now clusterInstance yamls go to resources section. Also a yaml file to define the namespace of the cluster name is required (kind: namespace etc.) for each cluster, and must be added to resources. If you are creating ConfigMaps and modifying template
Please read the articles and see how that is done.

4- Run the Playbook: This will migrate an Red Hat ACM (Advanced Cluster Management for Kubernetes) hub cluster version 2.12 and above for uste SiteConfig CR (SiteConfig files) to ClusterInstance CR/files. The ACM cluster must have spoke (managed) clusters installed originally based on siteConfig CR.
It is based on this Article: https://access.redhat.com/articles/7124143

Please update variables according to your situation.

5- a pause task has been added to the playbook so you can rename the files from kustomization.yaml to kustomization.yaml-siteConfigV1 , and kustomization.yaml-ClusterInstance to kustomization.yaml and push the change to git repo

In this code we applied the playbook on a cluster that has 2 cluster apps : clusters has a 3 nodes spoke cluster and a SNO, and a second clusters2 gitops Apps which handles another SNO.
For example: since I have run this playbook on a hub cluster with 2 Apps , I have 2 variables related to this and also 2 variables related to git repo. Maybe you need more , or only one.

