---
title: Plug-ins de controle do código-fonte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5a99ebdf2366ce6a60a6a724afc7d742db7150f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705798"
---
# <a name="source-control-plug-ins"></a>Plug-ins de controle do código-fonte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A seção de referência do SDK de controle do código-fonte contém a especificação da interface completa que permite que os sistemas de controle do código-fonte sejam integrados ao [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Ele especifica a sintaxe e a semântica das várias funções e tipos de dados que o plug-in de controle do código-fonte deve implementar para a interface com o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente de desenvolvimento integrado (IDE).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)  
 Lista as funções que devem ser implementadas pelo plug-in de controle do código-fonte para estar em conformidade com a API de plug-in de controle do código-fonte.  
  
 [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Descreve as funções que o plug-in de controle do código-fonte usa para passar informações para o IDE enquanto determinados comandos são executados.  
  
 [Enumeradores](../extensibility/enumerators.md)  
 Lista os tipos de dados do enumerador na API de plug-in de controle do código-fonte que o plug-in de controle do código-fonte deve conhecer.  
  
 [Sinalizadores de capacidade](../extensibility/capability-flags.md)  
 Descreve os `SCC_CAP_xxx` sinalizadores, que indicam os recursos de um provedor.  
  
 [Sinalizadores de bit usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md)  
 Lista os sinalizadores que são úteis no contexto de comandos específicos.  
  
 [Códigos de Erro](../extensibility/error-codes.md)  
 Lista os valores de erro comuns retornados pelas funções como `SCCTRN` .  
  
 [Cadeias de caracteres usadas como chaves para localizar um plug-in de controle do código-fonte](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Descreve as chaves para acessar o registro para localizar o plug-in de controle do código-fonte.  
  
 [Arquivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 Descreve um arquivo do lado do cliente que contém informações opacas para o IDE, mas que é usado pelo plug-in de controle do código-fonte para localizar a solução ou o projeto no controle de versão.  
  
 [Práticas recomendadas para implementar um plug-in de controle do código-fonte](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Fornece uma coleção de lembretes técnicos importantes a serem lembrados durante a implementação da API de plug-in de controle do código-fonte.  
  
 [Restrições de comprimentos de cadeia de caracteres](../extensibility/restrictions-on-string-lengths.md)  
 Descreve as limitações na API de plug-in de controle do código-fonte nos comprimentos das cadeias de caracteres usadas em várias funções.  
  
 [Glossário](../extensibility/source-control-plug-in-glossary.md)  
 Fornece os termos úteis e suas definições para ler a documentação do SDK de plug-in de controle do código-fonte.  
  
 [Como desativar avisos de compatibilidade para plug-ins de controle do código-fonte](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Descreve como desabilitar avisos.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Exemplo de plug-in de controle do código-fonte](https://msdn.microsoft.com/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Fornece um exemplo de funcionalidade de plug-in de controle do código-fonte.  
  
 [Guia de teste para plug-ins de controle do código-fonte](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Descreve os procedimentos de teste relacionados a um plug-in de controle do código-fonte.  
  
 [Criando um plug-in de controle do código-fonte](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Discute como criar um plug-in de controle do código-fonte que fornece funcionalidade de controle do código-fonte enquanto você está usando a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interface do usuário do controle do código-fonte (IU).  
  
 [Referência ao SDK do Visual Studio](../extensibility/visual-studio-sdk-reference.md)  
 Apresenta uma lista de tópicos de referência.
