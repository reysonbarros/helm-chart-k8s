##### Clonar o repositório do github
```
git clone https://github.com/badtuxx/giropops-senhas-labs.git
```

##### Criar o cluster
```
kind create cluster --config cluster.yaml
```

##### Listar o cluster 
```
kind get clusters
```

##### Listar os nodes do cluster de forma detalhada
```
k get node -o wide
```
 
##### Acessar o diretório abaixo do projeto clonado
```
cd giropops-senhas-labs/
```

##### Aplicar os recursos abaixo no cluster
```
k apply -f app-deployment.yaml
k apply -f app-service.yaml 
k apply -f redis-deployment.yaml 
k apply -f redis-service.yaml
```

##### Listar os serviços
```
k get svc
```

##### Listar os pods
```
k get pods
```
##### Exibir os logs do pod
```
k logs -f giropops-senhas-6848b6dd5b-4rf27
```

##### Executar o encaminhamento de portas entre host e service
```
k port-forward svc/giropops-senhas 5000:5000
```

##### Remover os services do giropops-senhas e redis
```
k delete svc giropops-senhas
k delete svc redis-service
```

##### Remover os deployments do giropops-senhas e redis
```
k delete deployment giropops-senhas
k delete deployment redis-deployment
```

##### Deploy do Helm Chart da aplicação. giropops-senhas refere-se ao nome da release(qualquer nome que desejar informar). ./ refere-se ao caminho onde o Chart.yaml foi criado
```
helm install giropops-senhas ./
```

##### Listar os Charts
```
helm list
```
##### Listar os Charts de uma namespace específica
```
helm list -n {namespace}
```

##### Exibir mais detalhes do Chart. A saída será os detalhes do Chart e os manifestos que foram renderizados pelo Helm.
```
helm get all giropops-senhas
```

##### Remover uma release do Chart
```
helm uninstall {release}
```
##### Atualizar o Chart
```
helm upgrade giropops-senhas ./
```

##### Listar o histórico de versões da release. Ao desinstalar(uninstall) uma release todo seu histórico é perdido.
```
helm history {release}
```
##### Rollback da release
```
helm rollback {release} {rev}
```
##### Comando para substituir um termo(String) por outro valor usando o Vi em nível global
```
:%s/.redis./.giropopsSenhas./g
```

##### Linting Helm Charts
```
helm lint {path_from_chart}
```
##### Renderiza os templates do helm
```
helm template {release}
```
##### Empacota um diretório do chart em um arquivo de chart no formato .tgz
```
helm package {path_from _chart}
```
##### Cria um index para os repositórios do helm chart
```
helm repo index --url https://github.com/reysonbarros/helm-chart-k8s .
```
##### Acessar o Settings do repo no github, realizar a config abaixo e clicar em Save. Source: Deploy from a branch. Branch: main root. Obs: Aguardar alguns instantes e atualizar a página para exibir a url(subdomínio) criada pelo github

##### Adicionando um repositório helm
```
helm repo add giropops-senhas-github https://reysonbarros.github.io/helm-chart-k8s/
```
##### Listando os repositórios helm
```
helm repo list
```
##### Pesquisar um repositório helm
```
helm search repo giropops-senhas-github
```
##### Exibir os detalhes do Chart.yaml e values.yaml referente ao helm repo
```
helm show all giropops-senhas-github/giropops-senhas
```
