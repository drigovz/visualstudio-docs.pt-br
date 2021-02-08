---
title: Tutorial do Docker – o que vem a seguir
description: Descreve as opções para estender os aplicativos Docker com orquestração, usando projetos de computação nativa de nuvem.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 8ca68b2eba710037535b4bd76c744e7c029a53e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841647"
---
# <a name="whats-next"></a>O que vem a seguir

Embora você tenha concluído seu tutorial, ainda há muito mais para aprender sobre contêineres!
Você não vai se aprofundar aqui, mas aqui estão algumas outras áreas a serem examinadas em seguida!

## <a name="container-orchestration"></a>Orquestração de contêineres

A execução de contêineres na produção é difícil. Você não deseja fazer logon em um computador e simplesmente executar um `docker run` ou `docker-compose up` . Por que não? Bem, o que acontece se os contêineres morrem? Como você dimensiona em vários computadores? A orquestração de contêiner resolve esse problema. Ferramentas como kubernetes, Swarm, Nomad e AKS todos ajudam a resolver esse problema, de maneira ligeiramente diferente.

A ideia geral é que você tem "gerentes" que recebem o **estado esperado**. Esse Estado pode ser "Eu quero executar duas instâncias do meu aplicativo Web e expor a porta 80." Em seguida, os gerentes examinam todos os computadores no cluster e delegam trabalho aos nós "Worker". Os gerentes observam alterações (como um contêiner encerrando) e, em seguida, funcionam para que o **estado real** reflita o estado esperado.

## <a name="cloud-native-computing-foundation-projects"></a>Projetos de computação nativa na nuvem

O CNCF é uma casa neutra de fornecedor para vários projetos de software livre, incluindo kubernetes, Prometheus, Envoy, Linkerd, NATS e muito mais! Você pode exibir os [projetos graduados e incubateddos aqui](https://www.cncf.io/projects/) e todo o [panorama de CNCF aqui](https://landscape.cncf.io/). Há muitos projetos para ajudar a resolver problemas de monitoramento, registro em log, segurança, registros de imagem, mensagens e muito mais!

Portanto, se você for novo no panorama do contêiner e no desenvolvimento de aplicativos nativos de nuvem, bem-vindo! Conecte-se à Comunidade, faça perguntas e Continue aprendendo! Estamos empolgados para você!

## <a name="working-with-docker-in-vs-code"></a>Trabalhando com o Docker no VS Code

Saiba mais sobre como usar a extensão VS Code Docker:

- [Visão geral da extensão do Docker VS Code](https://code.visualstudio.com/docs/containers/overview)
- [Introdução ao Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Introdução ao Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Introdução ao .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Depurar aplicativos em contêineres](https://code.visualstudio.com/docs/containers/debug-common)
