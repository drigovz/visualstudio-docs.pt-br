---
title: Implementando um fornecedor de porta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152680"
---
# <a name="implementing-a-port-supplier"></a>Implementando um fornecedor de porta
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um fornecedor de porta fornece portas na solicitação para o SDM (Gerenciador de depuração de sessão). Um fornecedor de porta precisa ser implementado durante a depuração em um computador não DCOM ou quando um novo dispositivo precisa ter suporte. Por exemplo, para fornecer depuração para um telefone celular, você pode implementar um fornecedor de porta que fornece portas que se conectam ao telefone celular (talvez por meio de IR ou uma conexão de célula) e enumeram os processos e programas em execução no telefone.  
  
 Para depurar programas em computadores baseados no Windows (incluindo depuração remota), o Visual Studio fornece fornecedores de porta para processos nativos e CLR (Common Language Runtime), portanto, não há necessidade de implementar seu próprio fornecedor de porta nesses casos.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementar e registrar um fornecedor de porta](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Discute como o SDM interage com o fornecedor da porta e suas portas.  
  
 [Interfaces de fornecedor porta necessárias](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Documenta as interfaces que devem ser implementadas para obter um fornecedor de porta.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)  
 Descreve os principais conceitos de arquitetura da depuração.  
  
## <a name="see-also"></a>Consulte Também  
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
