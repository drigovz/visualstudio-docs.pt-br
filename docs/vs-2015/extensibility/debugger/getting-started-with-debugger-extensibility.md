---
title: Introdução com extensibilidade do depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152705"
---
# <a name="getting-started-with-debugger-extensibility"></a>Introdução à extensibilidade do depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] fornece as informações que você deve ter para criar e personalizar os componentes do depurador usados para depurar programas de dentro do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a depuração adicionou melhorias derivadas do extensivo teste de usabilidade realizado em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuradores anteriores. Você pode usar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a depuração para percorrer um aplicativo em vários idiomas ou pode implementar a edição imediata de variáveis durante a depuração de aplicativos e soluções de vários idiomas.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a depuração é executada fora do processo com o programa que está sendo depurado e, portanto, é menos invasiva no espaço de processo do aplicativo. Consequentemente, é mais fácil escrever componentes que interajam com o depurador sem afetar o programa de depuração.  
  
 Para usar melhor o [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , você deve estar familiarizado com o seguinte:  
  
- O [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente de desenvolvimento integrado (IDE)  
  
- A linguagem de programação C++  
  
- COM ATL  
  
## <a name="in-this-section"></a>Nesta seção  
 [Roteiro para estender o depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Descreve o processo de implementação da depuração em seu produto, dependendo do seu compilador e de sua saída.  
  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)  
 Fornece uma visão geral dos [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componentes de depuração, que incluem o mecanismo de depuração, o avaliador de expressão (EE) e o manipulador de símbolo (SH).  
  
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)  
 Descreve os principais conceitos de arquitetura da depuração.  
  
 [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica como o mecanismo de depuração (DE) opera simultaneamente nos contextos de avaliação de código, documentação e expressão. Descreve, para cada um dos três contextos, o local, a posição ou a avaliação relevante para ele.  
  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)  
 Contém links para várias tarefas de depuração, como iniciar um programa e avaliar expressões.
