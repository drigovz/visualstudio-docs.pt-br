---
title: Usando o Gerenciador de texto para monitorar as configurações globais | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ece51450b8344ae4715a912399ec538171a26a5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695463"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Usar o gerenciador de texto para monitorar as configurações globais
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se você implementar um editor principal, deverá monitorar as alterações feitas nas configurações globais, pois essas alterações podem afetar sua instância do editor. Você pode acompanhar as alterações ouvindo eventos gerados pelo Gerenciador de texto. Por exemplo, quando você especifica uma preferência global para a aparência ou comportamento de um componente no editor principal, como seu objeto de dados de documento, o Gerenciador de texto armazena essas informações e as comunica para todos os clientes afetados.  
  
## <a name="text-manager-functions"></a>Funções do Gerenciador de texto  
 O Gerenciador de texto gera eventos para várias configurações, incluindo o seguinte:  
  
- Se um buffer está sob controle do código-fonte  
  
- Como registrar-se para notificações de alteração de arquivo  
  
- Como acompanhar quais modos de exibição estão associados a determinados buffers  
  
- Preferências de colorização de texto  
  
- Preferências de tabulação versus espaço  
  
  As preferências exclusivas de um determinado idioma não são gerenciadas pelo Gerenciador de texto. Essas configurações devem ser gerenciadas por cada serviço de idioma.  
  
  A notificação de eventos para o Gerenciador de texto é fornecida pela <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> interface. Implemente essa interface no objeto de cliente para manipular eventos gerados pelo Gerenciador de texto. Registre-se nesses eventos usando a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interface no Gerenciador de texto.  
  
## <a name="see-also"></a>Consulte Também  
 [Dentro do editor principal](../extensibility/inside-the-core-editor.md)   
 [Recursos do Editor](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
