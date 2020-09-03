---
title: Portas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73003e00fef5c37db4a702e7a4a1121600673844
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153696"
---
# <a name="ports"></a>Portas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em termos da arquitetura do depurador, uma **porta**:  
  
- É um contêiner para um conjunto de processos em execução em um servidor. Por exemplo, uma porta pode representar uma conexão com um dispositivo baseado em Windows CE por um cabo serial ou um computador não DCOM em rede. Uma porta especial, chamada de porta local, contém todos os processos em execução no computador local.  
  
- Pode se identificar por nome ou identificador.  
  
- Pode enumerar todos os processos em execução na porta e iniciar e encerrar esses processos.  
  
- É representado por uma interface [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , que é criada passando um argumento [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) para [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornece uma porta padrão que manipula todos os processos baseados no Windows, nativos e gerenciados. Uma porta personalizada deve ser implementada para conexões com dispositivos externos que não são baseados no Windows. Para fornecer essas portas personalizadas, um fornecedor de porta personalizado também precisa ser implementado.  
  
## <a name="see-also"></a>Consulte Também  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processar](../../extensibility/debugger/processes.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
