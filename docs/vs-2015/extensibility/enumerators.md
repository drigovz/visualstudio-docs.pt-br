---
title: Enumeradores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65a03a8dc741ec86aca3137f49cd753722ede215
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204564"
---
# <a name="enumerators"></a>Enumeradores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta seção lista os tipos de dados do enumerador na API de plug-in de controle do código-fonte que o plug-in de controle do código-fonte deve conhecer.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Código de comando](../extensibility/command-code-enumerator.md)  
 Enumera as opções para as funções [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md) .  
  
 [Mensagem](../extensibility/message-enumerator.md)  
 Enumera sinalizadores usados para o retorno de chamada de impressão, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Código de status do arquivo](../extensibility/file-status-code-enumerator.md)  
 Contém valores de constantes nomeados que especificam o estado de um arquivo sob controle do código-fonte.  
  
 [Código de status do diretório](../extensibility/directory-status-code-enumerator.md)  
 Contém valores de constantes nomeados que especificam o estado de um diretório sob controle do código-fonte.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criando um plug-in de controle do código-fonte](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define o SDK de plug-in de controle do código-fonte e descreve os recursos incluídos.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Solicita ao usuário as opções avançadas para o comando fornecido.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examina a lista de arquivos em busca de seu status atual. Além disso, o usa a `pfnPopulate` função para notificar o chamador quando um arquivo não corresponde aos critérios para o `nCommand` .  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Descreve a função de retorno de chamada usada pelo [SccOpenProject](../extensibility/sccopenproject-function.md) para exibir mensagens do plug-in de controle do código-fonte por meio do IDE.  
  
 [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)  
 Fornece uma listagem completa de todos os elementos na API de plug-in de controle do código-fonte.
