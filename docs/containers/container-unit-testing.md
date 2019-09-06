---
title: Teste de unidade em um aplicativo em contêineres
author: ghogen
description: Executar testes de unidade com cada compilação para um projeto do Docker no Visual Studio
ms.author: ghogen
ms.date: 06/17/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: ec5aea44362cf82f6745671cc0706f80e01a60ad
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "70312184"
---
# <a name="how-to-run-unit-tests-for-a-containerized-app"></a>Como: Executar testes de unidade para um aplicativo em contêineres

Você pode executar testes de unidade com cada compilação de seu projeto em contêineres modificando seu Dockerfile.

## <a name="prerequisites"></a>Pré-requisitos

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- Instalar o [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)
- Testes de unidade configurados para execução usando o [teste dotnet](/dotnet/core/tools/dotnet-test)
- Instalar a [extensão da janela contêineres](https://aka.ms/vscontainerspreview)

## <a name="add-unit-tests-to-the-dockerfile"></a>Adicionar testes de unidade ao Dockerfile

O Visual Studio faz algumas otimizações de desempenho especiais antes de modificar o Dockerfile. Ao criar a configuração de **depuração** , o Visual Studio cria projetos no computador local e copia os resultados para o contêiner. Portanto, somente o primeiro estágio do Dockerfile de multiestágio é executado conforme especificado no Dockerfile. Para saber mais, confira [processo de Build das ferramentas de contêiner para o Visual Studio](container-build.md).

Para adicionar testes de unidade a um Dockerfile de multietapa, `unit-test` adicione um estágio à Dockerfile entre `build` os `publish` estágios e.

```
FROM build AS unit-test
RUN dotnet unit-test --logger:trx
```

O Visual Studio só executa o primeiro estágio na configuração de **depuração** , `unit-test` portanto, o estágio só é executado na configuração de **versão** . Mas, mesmo na configuração da **versão** , os resultados do log não serão incluídos na imagem final, pois a imagem final é criada `base` a partir do palco `unit-test` , não a partir do palco. Para executar os testes e produzir uma imagem na qual você pode exibir os logs, use o seguinte comando:

```cmd
docker build --target:unit-test
```

## <a name="next-steps"></a>Próximas etapas

Em seguida, você pode usar a [janela contêineres](view-and-diagnose-containers.md) (se tiver a extensão instalada) para exibir os logs de teste.  

Para exibir os logs de teste, use **Ctrl**+**Q** e pesquise **contêineres** para abrir a janela **contêineres** . Na janela **contêineres** , localize o contêiner, abra a guia **arquivos** , procure o arquivo de resultados de teste (. trx) no sistema de arquivos do contêiner e abra-o para exibir os resultados no Visual Studio.

