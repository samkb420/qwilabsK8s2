    1  gcloud auth list
    2  gcloud config list project
    3  gcloud config set compute/zone us-central1-a
    4  gsutil -m cp -r gs://spls/gsp053/orchestrate-with-kubernetes .
    5  cd orchestrate-with-kubernetes/kubernetes
    6  kubectl explain deployment
    7  kubectl explain deployment --recursive
    8  kubectl explain deployment.metadata.name
    9  gcloud container clusters create bootcamp --num-nodes 5 --scopes "https://www.googleapis.com/auth/projecthosting,storage-rw"
   10  ls
   11  cd deployments/
   12  ls
   13  cd ..
   14  nano deployments/auth.yaml 
   15  kubectl create -f deployments/auth.yaml
   16  kubectl get deployments
   17  kubectl get replicasets
   18  kubectl get pods
   19  kubectl create -f services/auth.yaml
   20  kubectl create -f deployments/hello.yaml
   21  kubectl create -f services/hello.yaml
   22  kubectl create secret generic tls-certs --from-file tls/
   23  kubectl create configmap nginx-frontend-conf --from-file=nginx/frontend.conf
   24  kubectl create -f deployments/frontend.yaml
   25  kubectl create -f services/frontend.yaml
   26  kubectl get services frontend
   27  curl -ks https://`kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"`
   28  kubectl explain deployment.spec.replicas
   29  kubectl scale deployment hello --replicas=5
   30  kubectl get pods | grep hello- | wc -l
   31  kubectl scale deployment hello --replicas=3
   32  kubectl get pods | grep hello- | wc -l
   33  KUBE_EDITOR=nan0 kubectl edit deployment hello
   34  KUBE_EDITOR=nano kubectl edit deployment hello
   35  ls
   36  cd orchestrate-with-kubernetes/
   37  ls
   38  cd kubernetes/
   39  ls
   40  KUBE_EDITOR=nano kubectl edit deployment hello
   41  kubectl get replicaset
   42  kubectl rollout history deployment/hello
   43  kubectl rollout status deployment/hello
   44  kubectl rollout resume deployment/hello
   45  kubectl get pods -o jsonpath --template='{range .items[*]}{.metadata.name}{"\t"}{"\t"}{.spec.containers[0].image}{"\n"}{end}'
   46  kubectl rollout resume deployment/hello
   47  kubectl rollout status deployment/hello
   48  kubectl rollout undo deployment/hello
   49  kubectl get pods -o jsonpath --template='{range .items[*]}{.metadata.name}{"\t"}{"\t"}{.spec.containers[0].image}{"\n"}{end}'
   50  kubectl create -f deployments/hello-canary.yaml
   51  kubectl get deployments
   52  curl -ks https://`kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"`/version
   53  kubectl apply -f services/hello-blue.yaml
   54  kubectl create -f deployments/hello-green.yaml
   55  curl -ks https://`kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"`/version
   56  kubectl apply -f services/hello-green.yaml
   57  curl -ks https://`kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"`/version
   58  kubectl apply -f services/hello-blue.yaml
   59  curl -ks https://`kubectl get svc frontend -o=jsonpath="{.status.loadBalancer.ingress[0].ip}"`/version
   60  clear
   61  history
   62  history >Commandkube.md
