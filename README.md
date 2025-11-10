# openshift-acm-gitops-examples

Step 1:
- Login to the ACM cluster using `oc` CLI

Step 2:
- Create a new namespace for ACM policies (if the namespace does not exist)

```bash
oc create ns acm-policies
```

Step 3:
- Generate the policy file (assuming PolicyGenerator binary is already present at the location: 
`~/.config/kustomize/plugin/policy.open-cluster-management.io/v1/policygenerator/PolicyGenerator`)
- Policy is already generated under name (`generated-policy.yaml`)

```bash
kustomize build . --enable-alpha-plugins -o policies/gitops-operator/generated-policy.yaml
```

Step 4:
- Apply the policy

```bash
oc apply -f generated-policy.yaml
```
