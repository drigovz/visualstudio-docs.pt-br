---
title: Criação de perfil e segurança do Windows Vista | Microsoft Docs
description: Dependendo das configurações de permissões de acesso do usuário que estão disponíveis, um usuário individual pode ter permissão de segurança para criar o perfil de um processo nesse computador.
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0419ae09f2b43b396062fc8a3232b0a63c81483c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936386"
---
# <a name="profiling-and-windows-vista-security"></a>Criação de perfil e segurança do Windows Vista

Dependendo das configurações de Permissões de Acesso do Usuário do [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] que um administrador de computador disponibilizou, um usuário individual pode ter a permissão de segurança para analisar um processo no computador. Os exemplos a seguir ilustram possíveis diferenças entre os usuários:

- Alguns usuários podem acessar recursos de criação de perfil avançados quando o administrador tiver configurado o início do driver e do serviço.

- Os usuários do domínio podem acessar apenas as amostras de criação de perfil.

- Alguns usuários podem negar acesso à criação de perfil para todos os outros usuários.

  Para obter mais informações, consulte as opções de ADMIN em [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="cross-session-profiling"></a>Criação de perfil de sessão cruzada

A *criação de perfil de sessão cruzada* é a capacidade de criar o perfil de um processo que é executado em uma sessão de usuário diferente. Por exemplo, a maioria dos serviços são executados na sessão 0 e os usuários não podem ser executados diretamente na sessão 0. Usando o botão **Anexar ao Processo** na barra de ferramentas do Gerenciador de Desempenho ou a opção `/attach` da ferramenta de linha de comando VSPerfCmd, é possível analisar a maioria dos processos em sessões de usuário diferentes.

Você pode ver uma lista dos processos que estão disponíveis, definindo as opções de visibilidade de criação de perfil de processo cruzado. Essas opções estão disponíveis na janela **Anexar ao processo** que é exibida quando você seleciona **Anexar ao Processo**:

- **Mostrar processos de todos os usuários**

  Quando essa opção não está selecionada, a lista exibe apenas os processos pertencentes ao usuário atual. Caso contrário, a lista exibe os processos de todos os usuários.

- **Exibir processos em todas as sessões**

  Quando essa opção não está selecionada, a lista exibe os processos na sessão atual. Caso contrário, a lista exibe os processos em todas as sessões.

## <a name="see-also"></a>Confira também

- [Visões gerais](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Como: anexar a um processo em execução](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
