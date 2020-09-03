---
title: Usando KubernetesLocalProcessConfig. YAML para configuração adicional com o para o processo local com kubernetes
services: azure-dev-spaces
ms.date: 07/28/2020
ms.topic: conceptual
description: Descreve as opções de configuração adicionais para o processo local com kubernetes usando KubernetesLocalProcessConfig. YAML
keywords: Processo local com kubernetes, Azure Dev Spaces, espaços de desenvolvimento, Docker, kubernetes, Azure, AKS, serviço kubernetes do Azure, contêineres
monikerRange: '>=vs-2019'
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: 234eacedbc08007ede6bb5745a1a289aa838cccb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87508296"
---
# <a name="configure-local-process-with-kubernetes"></a>Configurar o processo local com o Kubernetes

O `KubernetesLocalProcessConfig.yaml` arquivo permite replicar as variáveis de ambiente e os arquivos montados disponíveis para o pods em seu cluster AKs. Você pode especificar as seguintes ações em um `KubernetesLocalProcessConfig.yaml` arquivo:

* Baixe um volume e defina o caminho para esse volume como uma variável de ambiente.
* Torne um serviço em execução no cluster disponível para processos em execução no seu computador de desenvolvimento.
* Crie uma variável de ambiente com um valor constante.

Um `KubernetesLocalProcessConfig.yaml` arquivo padrão não é criado automaticamente, portanto, você deve criar manualmente o arquivo na raiz do seu projeto.

## <a name="download-a-volume"></a>Baixar um volume

Em *env*, especifique um *nome* e um *valor* para cada volume que você deseja baixar. O *nome* é a variável de ambiente que será usada no seu computador de desenvolvimento. O *valor* é o nome do volume e um caminho no computador de desenvolvimento. O valor de *Value* assume a forma *$ (volumeMounts: VOLUME_NAME)/Path/to/Files*.

Por exemplo:

```yaml
version: 0.1
env:
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
```

O exemplo acima baixa o volume de *lista de permissões* do contêiner e define esse local mais o caminho para a variável de ambiente *ALLOW_LIST_PATH*. O comportamento padrão é baixar os arquivos para o caminho especificado em um diretório temporário no seu computador de desenvolvimento. No exemplo acima, *ALLOW_LIST_PATH* é definido como `/TEMPORARY_DIR/allow-list` . 

> [!NOTE]
> O download de um volume baixará todo o conteúdo desse volume, independentemente do caminho definido. O caminho é usado apenas para definir a variável de ambiente para uso no computador de desenvolvimento. Adicionar */Allow-List* ou */path/to/Files* ao final do token não afeta realmente o local em que o volume é persistido. A variável de ambiente é apenas uma conveniência caso seu aplicativo precise de uma referência a um arquivo específico dentro desse volume.

Você também tem a opção de especificar um local para baixar a montagem de volume em seu computador de desenvolvimento em vez de usar um diretório temporário. Em *volumeMounts*, especifique um *nome* e *LocalPath* para cada local específico. O *nome* é o nome do volume que você deseja corresponder e *LocalPath* é o caminho absoluto no seu computador de desenvolvimento. Por exemplo:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
```

O exemplo acima usa a entrada em *env* para baixar um volume que corresponda ao *padrão- \* token-*, como *Default-token-1111* ou *Default-token-1234-5678-90abcdef*. Nos casos em que vários volumes correspondem, o primeiro volume correspondente é usado. Todos os arquivos são baixados para `/var/run/secrets/kubernetes.io/serviceaccount` no seu computador de desenvolvimento usando a entrada em *volumeMounts*. A variável de ambiente *KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE* é definida como `/var/run/secrets/kubernetes.io/serviceaccount` .

## <a name="make-a-service-available"></a>Disponibilizar um serviço

Em *env*, especifique um *nome* e um *valor* para cada serviço que você deseja disponibilizar em seu computador de desenvolvimento. O *nome* é a variável de ambiente que será usada no seu computador de desenvolvimento. O *valor* é o nome do serviço do seu cluster e um caminho. O valor de *Value* assume a forma *$ (Services: service_name)/Path*.

Por exemplo:

```yaml
version: 0.1
env:
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
```

O exemplo acima disponibiliza o serviço *myapp1* para o seu computador de desenvolvimento e a variável de ambiente *MYAPP1_SERVICE_HOST* é definida como o endereço IP local do serviço *myapp1* com o `/api/v1` caminho (ou seja, `127.1.1.4/api/v1` ). O serviço *myapp1* é acessível usando a variável de ambiente, *myapp1*ou *myapp1. svc. cluster. local*.

> [!NOTE]
> Tornar um serviço disponível em seu computador de desenvolvimento tornará todo o serviço disponível, independentemente do caminho definido. O caminho é usado apenas para definir a variável de ambiente para uso no computador de desenvolvimento.
Você também pode tornar um serviço de um namespace kubernetes específico disponível usando *$ (Services: service_name. NAMESPACE_NAME)*. Por exemplo:

```yaml
version: 0.1
env:
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
```

O exemplo acima torna o *myapp2* do namespace *MyNamespace* disponível em seu computador de desenvolvimento e define a variável de ambiente *MYAPP2_SERVICE_HOST* para o endereço IP local do *myapp2* do namespace *MyNamespace* .

## <a name="create-an-environment-variable-with-a-constant-value"></a>Criar uma variável de ambiente com um valor constante

Em *env*, especifique um *nome* e um *valor* para cada variável de ambiente que você deseja criar em seu computador de desenvolvimento. O *nome* é a variável de ambiente que será usada no seu computador de desenvolvimento e o *valor* é o valor. Por exemplo:

```yaml
version: 0.1
env:
  - name: DEBUG_MODE
    value: "true"
```

O exemplo acima cria uma variável de ambiente chamada *DEBUG_MODE* com um valor de *true*.

## <a name="example-kuberneteslocalprocessconfigyaml"></a>Exemplo KubernetesLocalProcessConfig. YAML

Aqui está um exemplo de um `KubernetesLocalProcessConfig.yaml` arquivo completo:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
  - name: DEBUG_MODE 
    value: "true"
```

## <a name="next-steps"></a>Próximas etapas

Para começar a usar o processo local com o kubernetes para se conectar ao seu computador de desenvolvimento local ao cluster, consulte [usar o processo local com o kubernetes com o Visual Studio Code][local-process-kubernetes-vs-code] e [usar o processo local com o kubernetes com o Visual Studio][local-process-kubernetes-vs].

[local-process-kubernetes-vs-code]: https://code.visualstudio.com/docs/containers/local-process-kubernetes
[local-process-kubernetes-vs]: local-process-kubernetes.md
