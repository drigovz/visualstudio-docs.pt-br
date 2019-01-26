---
title: Enumeradores | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e57f11f61a1bcb2372a07e34167ecacd324067c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037782"
---
# <a name="enumerators"></a>Enumeradores
Esta seção lista os tipos de dados em que a API de plug-in de controle do código-fonte que o plug-in de controle do código-fonte deve saber sobre enumerador.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Código de comando](../extensibility/command-code-enumerator.md)  
 Enumera as opções para o [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md) funções.  
  
 [Message](../extensibility/message-enumerator.md)  
 Enumera os sinalizadores usados para o retorno de chamada, impressão [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Código de status do arquivo](../extensibility/file-status-code-enumerator.md)  
 Contém valores constantes nomeados que especificam o estado de um arquivo sob controle do código-fonte.  
  
 [Código de status do diretório](../extensibility/directory-status-code-enumerator.md)  
 Contém valores constantes nomeados que especificam o estado de um diretório sob controle do código-fonte.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criar um controle de fonte plug-in](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define o SDK do plug-in de controle de origem e descreve os recursos incluídos.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Solicita ao usuário para opções avançadas para o comando fornecido.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examina a lista de arquivos para seu status atual. Além disso, usa o `pfnPopulate` função para notificar o chamador quando um arquivo não coincide com os critérios para o `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Descreve a função de retorno de chamada que é usada pelo [SccOpenProject](../extensibility/sccopenproject-function.md) para exibir mensagens de controle de fonte de plug-in por meio do IDE.  
  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)  
 Fornece uma lista completa de todos os elementos na API de plug-in de controle de origem.