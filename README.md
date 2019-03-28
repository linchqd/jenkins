# jenkins master

  kubectl-cert-cm.yaml:

  kubectl create configmap kubectl-cert-cm --from-file=/etc/kubernetes/cert/ca.pem \
	--from-file=/etc/kubernetes/cert/admin.pem \
	--from-file=admin.key=/etc/kubernetes/cert/admin-key.pem \
	--dry-run -o yaml > kubectl-cert-cm.yaml


