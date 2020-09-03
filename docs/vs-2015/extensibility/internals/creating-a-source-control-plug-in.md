---
title: Criando um plug-in de controle do código-fonte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 37cb4cfc71b2574600bf7ca886c693b888ec821a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196974"
---
# <a name="creating-a-source-control-plug-in"></a>Criando um plug-in de controle do código-fonte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O SDK do Visual Studio fornece recursos que permitem que você adicione a funcionalidade de controle do código-fonte ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (ambiente de desenvolvimento integrado). Ele permite que você use qualquer DLL de plug-in que esteja em conformidade com a API de plug-in de controle do código-fonte descrita nesta documentação.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 Descreve como instalar um plug-in de controle do código-fonte e realça as versões da API de plug-in de controle do código-fonte disponíveis no momento.  
  
 [Arquitetura](../../extensibility/internals/source-control-plug-in-architecture.md)  
 Usa um diagrama de arquitetura para explicar a integração de um plug-in de controle do código-fonte com o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Guia de teste para plug-ins de controle do código-fonte](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Fornece orientação sobre como testar a instalação e a operação de um plug-in de controle do código-fonte.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Discute como criar um VSPackage de controle do código-fonte que não só fornece funcionalidade de controle de origem, mas substitui a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] interface do usuário do controle do código-fonte.  
  
 [Plug-ins de controle do código-fonte](../../extensibility/source-control-plug-ins.md)  
 Fornece uma listagem completa de todos os elementos na API de plug-in de controle do código-fonte.  
  
 [Controle do código-fonte](../../extensibility/internals/source-control.md)  
 Discute as opções para implementar o controle do código-fonte como um recurso integrado do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
