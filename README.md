# KUBERNETES - CRIANDO QUEUE, TOPIC e SUBSCRIPTION NO IBM MQ

Ao utilizar o IBM MQ da IBM, foi determinado que será necessário a criação de Queue, Topic e Subscriptions no momento da criação do conteiner e não há a necessidade de persitir o conteúdo destes objetos quando os containers foram destruídos.

Devido a simplicidade da tarefa, todos os objetos do Kuberntes serão criados em um único arquivo de manifesto YAML.

Os objetos a serem criados são:

* Deployment
* Service
* ConfigMap

A solução apresentada foi a criação das Queue, Topic e Subscriptions dentro do objeto ConfigMap, já no objeto Deployment, o conteúdo da tag DATA é convertida para volumes que serão montados como arquivos dentro da pasta /mnt/mqm/, dentro do POD para ser inicializado no momento da criação do POD.
