---
title: Introdução com plug-ins de controle do código-fonte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85aa5727f252ad75c45064d7b885e3d282da36a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538155"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Introdução aos plug-ins do controle do código-fonte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para criar um plug-in de controle do código-fonte, você deve criar uma DLL que implemente as funções definidas na API de plug-in de controle do código-fonte e, em seguida, registrar a DLL com [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para disponibilizá-la para uso no controle de versão do código-fonte.  
  
 Três versões da API de plug-in de controle do código-fonte (versões 1,1, 1,2 e 1,3) estão disponíveis para plug-ins de controle do código-fonte. A API de plug-in de controle do código-fonte documentada aqui é a versão 1,3. Ele foi projetado para ser totalmente compatível com os plug-ins de controle do código-fonte que dão suporte às versões 1,1 e 1,2. A seção o que há de [novo na API de plug-in de controle do código-fonte versão 1,3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) detalha os novos recursos com suporte na versão mais recente da API de plug-in de controle do código-fonte.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como instalar um plug-in de controle do código-fonte](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Descreve como fazer as entradas do registro que são necessárias para conectar uma DLL de controle do código-fonte.  
  
 [Novidades na API do plug-in de controle do código-fonte versão 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Fornece uma breve visão geral das alterações que foram feitas na API de plug-in de controle do código-fonte na versão 1,3.  
  
 [Novidades na API do plug-in de controle do código-fonte versão 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Fornece uma breve visão geral das alterações que foram feitas na API de plug-in de controle do código-fonte na versão 1,2.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Plug-ins de controle do código-fonte](../../extensibility/source-control-plug-ins.md)  
 Fornece uma listagem completa de todos os elementos na API de plug-in de controle do código-fonte.  
  
 [Criando um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define o SDK de plug-in de controle do código-fonte e descreve os recursos incluídos.
